## Characteristics

- Introduces specific improvements to overcome the limitations of [[Naive RAG]]
- Employs pre-retrieval and post-retrieval strategies to enhance [[retrieval]] quality
- Refines the [[indexing]] techniques through the use of a sliding window approach, fine-grained segmentation, and the incorporation of metadata
- Incorporates several optimization methods to streamline the [[retrieval]] process

## Pre-retrieval process

- Optimize the [[indexing]] structure and to enhance the quality of the content being indexed
	- Enhancing data granularity
	- Optimizing index structures
	- Adding metadata
	- Alignment optimization
	- Mixed retrieval
- Optimize the user query to make the question clearer and more suitable for the [[retrieval]] task
	- Query rewriting
	- Query transformation
	- Query expansion

## Post-retrieval process

- Chunks reranking
	- Re-rank the retrieved information to relocate the most relevant content to the edges of the prompt
	- Implemented in LangChain, LlamaIndex, HayStack
- Context compressing
	- Concentrate on selecting the essential information, emphasizing critical sections, and shortening the context to be processed
	- Prevent overloading LLMs and diluting the focus on key details with irrelevant content

