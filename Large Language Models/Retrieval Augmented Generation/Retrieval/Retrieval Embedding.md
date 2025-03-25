## Characteristics

- The semantic representation capability of embedding models plays a key role

## Mix/hybrid retrieval

- Sparse and dense embedding approaches capture different relevance features
- Can benefit from each other by leveraging complementary relevance information
- Sparse [[retrieval]] models can enhance the zero-shot retrieval capability of dense retrieval models and assist dense retrievers in handling queries containing rare entities

## Fine-tuning embedding model

- Supplement domain knowledge in which the context significantly deviates from pre-training corpus
- Align the retriever and generator
- E.g. LM-supervised retriever (LSR), Promptagator, LLM-Embedder, REPLUG
