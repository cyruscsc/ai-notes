## Definition

- A training architecture whereby each input word is passed through a neural network simultaneously

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

- Parallel processing is possible
- The calculations are fast and accurate

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




