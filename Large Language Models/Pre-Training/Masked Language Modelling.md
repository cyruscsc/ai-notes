---
aliases:
  - MLM
---

## Definition

- Predict the masked tokens based on the surrounding context

## Characteristics

- Primarily used in encoder-only models like `BERT`
- Random tokens or spans of tokens in the input text are replaced with a special `[MASK]` token
- Typically, about 15% of words in input sentences are masked during [[pre-training]]
- Allows the model to learn bidirectional context, considering both preceding and following words when making predictions
