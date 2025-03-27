---
aliases:
  - RAPTOR
---

## Definition

- Constructs a hierarchical structure of documents, allowing for more efficient and context-aware information retrieval

## Process

1. Split text into manageable chunks
2. Generate embeddings for text chunks
3. Construct the hierarchical tree
	- Cluster similar chunks of text
	- Create summaries for each cluster
	- Generate embeddings for summaries
	- Repeat the process recursively, moving up the tree
4. Store the entire tree structure, including original chunks and summaries, in a vector store

## Retrieval mechanisms

### Tree traversal retrieval

- Systematically explores the tree structure
- Starts from the root and progresses down relevant branches

### Collapsed tree retrieval

- Treats the tree as a single layer
- Compares query embeddings directly to all node embeddings
- Useful for specific, factual queries

## Benefits

- Captures broader context and improves representation of large-scale discourse
- Enables faster and more relevant information retrieval
- Can handle both low-level factual queries and high-level conceptual questions
- Outperforms traditional retrieval methods on various question-answering tasks

## Code example

- See [LangChain cookbook](https://github.com/langchain-ai/langchain/blob/master/cookbook/RAPTOR.ipynb)
