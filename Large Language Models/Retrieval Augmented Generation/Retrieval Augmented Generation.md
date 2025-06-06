---
aliases:
  - RAG
---

## Definition

- Enhances the capabilities of [[large language models]] by incorporating external information retrieval
- Allows AI models to access and utilize up-to-date or domain-specific information beyond their original training data, resulting in more accurate and contextually relevant responses

## Map

- [[RAG Paradigms]]
	- [[Naive RAG]]
	- [[Advanced RAG]]
	- [[Modular RAG]]
- [[Query Translation]]
	- [[Multi-Query]]
	- [[RAG-Fusion]]
	- [[Reciprocal Rank Fusion|RRF]]
	- [[Decomposition]]
	- [[Least-to-Most Prompting|LtM]]
	- [[Iterative Retrieval Chain-of-Thought|IR-CoT]]
	- [[Step-Back Prompting]]
	- [[Hypothetical Document Embeddings|HyDE]]
- [[Routing]]
	- [[Logical Routing]]
	- [[Semantic Routing]]
	- [[Embedding Router]]
	- [[LLM Router]]
- [[Query Construction]]
	- [[Query Structuring for Metadata Filters]]
 - [[Indexing]]
	 - [[Multi-Representation Indexing]]
	- [[Proposition Indexing]]
	- [[Multi-Vector Retriever]]
	- [[Recursive Abstractive Processing for Tree-Organized Retrieval|RAPTOR]]
	- [[Contextualized Late Interaction BERT|ColBERT]]
	- [[Indexing Optimization]]
- [[Retrieval]]
	- [[Retrieval Source]]
	- [[Query Optimization]]
	- [[Retrieval Embedding]]
	- [[Retrieval Adapter]]
- [[Augmentation]]
	- [[Iterative Retrieval]]
	- [[Recursive Retrieval]]
	- [[Adaptive Retrieval]]
- [[Generation]]
	- [[Content Curation]]
	- [[Fine-Tuning]]
- [[RAG Evaluation]]
	- [[RAG Evaluation in General]]
	- [[Evaluation Targets]]
	- [[Evaluation Datasets]]
	- [[Evaluation Metrics]]
	- [[Evaluation Frameworks]]

## Benefits

- **Improved Accuracy**: Enables [[Large Language Models|LLMs]] to provide more accurate and up-to-date information by accessing external sources
- **Reduced Hallucinations**: Helps minimize AI hallucinations and factual errors by grounding responses in retrieved information
- **Cost-Efficiency**: Reduces the need for frequent model retraining, lowering computational and financial costs
- **Transparency**: Allows for the inclusion of source references, enabling users to verify information
- **Adaptability**: New information can be easily added to the external knowledge base without retraining the entire model
