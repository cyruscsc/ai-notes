## Characteristics

```plaintext
              ┌─┐ ┌─┐  ┌─┐┐  ┌─┐  ┌─┐
           ┌──│I│+│P│─→│S││─→│N│─→│R│
           │  └─┘ └─┘  └─┘┘  └─┘  └─┘
           │
           │  ┌─┐ ┌─┐  ┌─┐┐  ┌─┐  ┌─┐
           ├──│I│+│P│─→│S││─→│N│─→│R│
           │  └─┘ └─┘  └─┘┘  └─┘  └─┘
sequence ──┤
           │  ┌─┐ ┌─┐  ┌─┐┐  ┌─┐  ┌─┐
           ├──│I│+│P│─→│S││─→│N│─→│R│
           │  └─┘ └─┘  └─┘┘  └─┘  └─┘
           │
           │  ┌─┐ ┌─┐  ┌─┐┐  ┌─┐  ┌─┐
           └──│I│+│P│─→│S││─→│N│─→│R│
              └─┘ └─┘  └─┘┘  └─┘  └─┘
```

> `I`: input word
> `P`: positional encoding
> `S`: multi-headed [[Attention|self-attention]]
> `N`: neural network
> `R`: encoded representation

- Self-attention allows the model to weigh the importance of different parts of the input sequence
- Capable of capturing long-range dependencies and relationships between tokens efficiently
- Process entire sequences simultaneously, significantly reducing training time and improving scalability

## Types

- [[Encoder Models]]
- [[Decoder Models]]
- [[Encoder-Decoder Models]]



## Implementation

```plaintext
encoder
┌─┐ ┌─┐  ┌─┐┐  ┌─┐  ┌─┐
│I│+│P│─→│S││─→│N│─→│R│
└─┘ └─┘  └─┘┘  └─┘  └┬┘
                ┌────┘
decoder         │
┌─┐ ┌─┐  ┌─┐┐  ┌┴┐┐  ┌─┐  ┌─┐
│W│+│P│─→│S││─→│A││─→│N│─→│O│
└─┘ └─┘  └─┘┘  └─┘┘  └─┘  └─┘
```

> `I`: input word
> `P`: positional encoding
> `S`: multi-headed [[Attention|self-attention]]
> `N`: neural network
> `R`: encoded representation
> `W`: previous output word
> `A`: multi-headed [[Attention|attention]]
> `O`: next output word

## Pipeline

### Tokenizer

- Splits the input into tokens (words, subwords, or symbols)
- Maps each token to an integer (token ID)
- Adds additional inputs that may be useful to the model

### Model

- For each input from the tokenizer, outputs a hidden state (also known as features)
- The output of the Transformer model is sent directly to the model head to be processed

#### Hidden states

- Each hidden state captures the contextual understanding of that input by the Transformer model
- A hidden state is a high-dimensional vector that generally has three dimensions:
	- **Batch size**: The number of sequences processed at a time
	- **Sequence length**: The length of the numerical representation of the sequence
	- **Hidden size**: The vector dimension of each model input (commonly 768 for smaller models, 3072 or more for larger models)

#### Model heads

- Take the hidden states as input
- Project the hidden states into the appropriate dimensionality for a specific task
	- [[Classification]] tasks: Output logits corresponding to the number of classes
	- Language modeling: Output logits over the vocabulary size
- Usually implemented as one or more fully connected (linear) layers

### Postprocessing

- Output logits from model heads are unnormalized scores that need further processing
- [[Classification]] tasks: Passed through a [[softmax function]] to obtain probabilities
- Sequence generation tasks: Used with decoding techniques (e.g., greedy search, beam search)

## Components

### Encoding

- An input word goes into the neural network and is captured as an encoded representation
- Multi-headed self-attention and neural network steps can be repeated multiple times
	- Get a deeper representation 
	- Learn deeper patterns within the input text
- This process is repeated multiple times for each of the input words in the sequence

### Decoding

- The previous output word and its positional encoding are given to multiple self-attention steps and the neural network
- Multi-headed self-attention, multi-headed attention, and neural network steps can be repeated multiple times
- This process is repeated multiple times for each of the output words in the sequence

### Position encoding

- Added to the inputs and outputs as word order could easily be lost since all words are fed into the neural network at the same time
- Use both the word and the position of the word in the encoded representation

### Multi-headed self-attention

- Helps define the context of the word being inputted or outputted
- Pays attention to multiple facets at the same time
- Each attention head pays attention to something different
- In encoding step, pays attention to other input words to decide the encoded representation
- In decoding step, pays attention to other output words

### Multi-headed attention

- Fed the encoded representation from the encoding process
- Decide which of the encoded representation are relevant to generating the next token
- Pays attention to multiple facets at the same time
- Each attention head pays attention to something different

## Code examples

### Tokenizer

```python
from transformers import AutoTokenizer

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
tokenizer = AutoTokenizer.from_pretrained(checkpoint)

raw_inputs = [
    "I've been waiting for a HuggingFace course my whole life.",
    "I hate this so much!",
]
inputs = tokenizer(raw_inputs, padding=True, truncation=True, return_tensors="pt")

# input tokens
print(inputs)
```

### Model

```python
from transformers import AutoModel

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModel.from_pretrained(checkpoint)

outputs = model(**inputs)

# hidden state
print(outputs.last_hidden_state.shape)
```

### Model with sequence classification head

```python
from transformers import AutoModelForSequenceClassification

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModelForSequenceClassification.from_pretrained(checkpoint)

outputs = model(**inputs)

# logits
print(outputs.logits.shape)
```

### Postprocessing with softmax

```python
import torch

predictions = torch.nn.functional.softmax(outputs.logits, dim=-1)

# probabilities
print(predictions)
```