## Definition

- Creates a structured representation of external data for efficient retrieval

## Techniques

- [[Multi-Representation Indexing]]
	- [[Proposition Indexing]]
	- [[Multi-Vector Retriever]]
- [[Recursive Abstractive Processing for Tree-Organized Retrieval|RAPTOR]]
- [[Contextualized Late Interaction BERT|ColBERT]]

## Related issues

- [[Indexing Optimization]]

## Code example

```python
some_docs = "..."  # some documents  


# split

from langchain.text_splitter import RecursiveCharacterTextSplitter

text_splitter = RecursiveCharacterTextSplitter.from_tiktoken_encoder(
	chunk_size=300,
	chunk_overlap=50
)

splits = text_splitter.split_documents(some_docs)


# index

from langchain_openai import OpenAIEmbeddings
from langchain_community.vectorstores import Chroma

vectorstore = Chroma.from_documents(
	documents=splits,
	embedding=OpenAIEmbeddings()
)

retriever = vectorstore.as_retriever()
```
