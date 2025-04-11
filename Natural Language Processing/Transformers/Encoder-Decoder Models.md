---
aliases:
  - Sequence-to-Sequence Models
  - Seq2Seq Models
---

## Definition

- Use both parts of the Transformer architecture

## Characteristics

- At each stage, the [[attention]] layers of the encoder can access all the words in the initial sentence, whereas the attention layers of the decoder can only access the words positioned before a given word in the input
- The [[pre-training]] of these models can be done using the objectives of encoder or decoder models, but usually involves something a bit more complex
	- E.g., `T5` is pre-trained by replacing random spans of text with a single mask special word, and the objective is then to predict the text that this mask word replaces
- Best suited for tasks revolving around generating new sentences depending on a given input
	- E.g., summarization, translation, generative question answering

## Examples

- `BART`
- `mBART`
- `Marian`
- `T5`
