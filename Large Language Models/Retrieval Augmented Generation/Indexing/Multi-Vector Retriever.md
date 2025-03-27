## Definition

- Creates and utilizes multiple vector representations for each document

## Process

1. Extract different elements (text, tables, images) from documents
2. Generate summaries for each content type
3. Embed these summaries using appropriate models
4. Store the embeddings in a vector database, while keeping the original documents in a separate store
5. Perform similarity search on the embedded summaries
6. Retrieve the corresponding original documents for the most relevant summaries

## Benefits

- Maintains the relationship between text and associated images or tables
- Effectively handles multi-modal data, including text, tables, and images
