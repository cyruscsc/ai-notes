## Definition

- Captures distinct, minimal, and self-contained meanings within a text

## Process

1. Use an LLM to extract propositions from each document
2. Index the extracted propositions and link them to their underlying text
3. When a question is asked, the system retrieves the most relevant propositions along with their associated full text

## Benefits

- Outperforms sentence and passage-level retrieval
- Provides better context by retrieving propositions linked to full documents
- Allows for decoupling the chunk used for retrieval from the one used for synthesis, offering more flexibility in RAG systems
