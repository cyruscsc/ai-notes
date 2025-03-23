---
aliases:
  - FLM
  - Causal Language Modelling
  - CLM
---

## Definition

- Predict the next token in a sequence given all previous tokens

## Characteristics

- Typically used in decoder-only architectures
	- E.g., `GPT` series
- The model learns to generate text by predicting each subsequent word based on the context of all preceding words
- Maintains a unidirectional (left-to-right) [[attention]] pattern, where each token can only attend to previous tokens in the sequence
