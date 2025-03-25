## Definition

- Dynamically adjusts the [[retrieval]] strategy based on the complexity and requirements of the query

## Characteristics

- Enables [[Large Language Models|LLMs]] to actively determine the optimal moments and content for retrieval
- Enhances the efficiency and relevance of the information sourced
- Balances computational resources while maintaining response quality, adapting to dynamic environments
- E.g., FLARE, Self-RAG

## Process

1. Classify the complexity of the query using a decision mechanism
2. Choose between direct LLM response, single-step retrieval, or multi-step retrieval
3. Continuously optimize both retrieval and [[generation]] processes based on real-time feedback and changing data
