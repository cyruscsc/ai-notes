---
aliases:
  - PLM
---

## Definition

- Predict each token outside the prefix, given all previous tokens

## Characteristics

- Typically used in [[Encoder-Decoder]] and non-causal decoder-only models
- A random prefix of tokens is selected from the input sequence
- The attention mask is allowed to be non-causal within the prefix, enabling bidirectional [[Attention]] for those tokens
- During inference, the prefix naturally becomes the input text
