---
aliases:
  - Autoregressive Models
---

## Definition

- Use only the decoder of a Transformer model

## Characteristics

- At each stage, for a given word the [[attention]] layers can only access the words positioned before it in the sentence
- The [[pre-training]] of decoder models usually revolves around predicting the next word in the sentence
- Best suited for tasks involving text generation

## Examples

- `CTRL`
- `GPT`
- `GPT-2`
- `Transformer XL`
