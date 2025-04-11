---
aliases:
  - Autoencoding Models
---

## Definition

- Use only the encoder of a Transformer model

## Characteristics

- At each stage, the [[attention]] layers can access all the words in the initial sentence
- Often characterized as having "bi-directional" attention
- The [[pre-training]] of these models usually revolves around somehow corrupting a given sentence and tasking the model with finding or reconstructing the initial sentence
	- E.g., by masking random words in it
- Best suited for tasks requiring an understanding of the full sentence
	- E.g., sentence classification, word classification, named entity recognition, extractive question answering

## Examples

- `ALBERT`
- `BERT`
- `DistilBERT`
- `ELECTRA`
- `RoBERTa`
