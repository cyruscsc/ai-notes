## Characteristics

- LLM tends to only focus on the beginning and end of long texts
- Redundant information can interfere with the final [[generation]] of LLM
- Overly long contexts can also lead LLM to the "lost in the middle" problem
- Therefore, in the [[Retrieval Augmented Generation|RAG]] system, the retrieved content typically requires further processing

## Reranking

- Reorders document chunks to highlight the most pertinent results
- Reduces the overall document pool, acting as both an enhancer and a filter
- Delivers refined inputs for more precise language model processing
- **Rule-based methods**: depend on predefined metrics such as diversity, relevance, and MRR
- **Model-based methods**: such as [[encoder-decoder]] models, specialized reranking models, and [[Large Language Models|LLMs]]

## Context selection/compression

- Excessive context can introduce more noise, diminishing the LLM’s perception of key information
- Reducing the number of documents also helps improve the accuracy of the model’s answers
- Can utilize small language models (SLMs) to detect and remove unimportant tokens
- Can have the LLM evaluate the retrieved content before generating the final answer
- Can train an information condenser using contrastive learning, such as RECOMP
