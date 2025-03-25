## Characteristics

- Follows a traditional process that includes [[indexing]], [[retrieval]], and generation

## Indexing

- Clean and extract raw data
- Convert raw data into a uniform plain text format
- Segment the text into smaller, digestible chunks to accommodate the context limitations of language models
- Encode the chunks into vector representations using an embedding model
- Store the embeddings in vector database to enable efficient similarity searches

## Retrieval

- Encode the user query into a vector representation using the same embedding model
- Compute the similarity scores between the query vector and the vector of chunks within the indexed corpus
- Prioritize and retrieve the top `k` chunks that demonstrate the greatest similarity to the query
- Use these chunks as the expanded context in prompt

## Generation

- Synthesize the query and the selected documents into a coherent prompt to which a large language model is tasked with formulating a response
- The model’s approach to answering may vary depending on task-specific criteria
	- Can draw upon its inherent parametric knowledge
	- Can restrict its responses to the information contained within the provided documents
- In cases of ongoing dialogues, any existing conversational history can be integrated into the prompt

## Challenges

### Retrieval challenges

- The retrieval phase often struggles with precision and recall
- May lead to the selection of misaligned or irrelevant chunks, and the missing of crucial information

### Augmentation hurdles

- May encounter redundancy when similar information is retrieved from multiple sources
- Determining the significance and relevance of various passages
- Ensuring stylistic and tonal consistency
- Facing complex issues, a single retrieval based on the original query may not suffice to acquire adequate context information

### Generation difficulties

- The model may face the issue of [[hallucination]]
- Can also suffer from irrelevance, toxicity, or bias in the outputs
- Generation models might overly rely on augmented information, leading to outputs that simply echo retrieved content without adding insightful or synthesized information
