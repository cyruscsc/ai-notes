## Characteristics

- The quality of index construction determines whether the correct context can be obtained in the [[retrieval]] phase

## Chunking strategy

- Larger chunks can capture more context, but they also generate more noise, requiring longer processing time and higher costs
- Smaller chunks may not fully convey the necessary context, they do have less noise
- E.g., recursive chunking, sliding window chunking, Small2Big

## Metadata attachment

- Chunks can be enriched with metadata information
- [[Retrieval]] can be filtered based on this metadata, limiting the scope of the retrieval
- E.g., page number, timestamp, summary paragraph, Reverse HyDE

## Structural index

- Establish a hierarchical structure for the documents
- [[Retrieval Augmented Generation|RAG]] system can expedite the retrieval and processing of pertinent data

### Hierarchical index structure

- Files are arranged in parent-child relationships, with chunks linked to them
- Data summaries are stored at each node, aiding in the swift traversal of data and assisting the [[Retrieval Augmented Generation|RAG]] system in determining which chunks to extract

### Knowledge graph index

- Delineates the connections between different concepts and entities
- Transform the information [[retrieval]] process into instructions that LLM can comprehend
- E.g., KGP
