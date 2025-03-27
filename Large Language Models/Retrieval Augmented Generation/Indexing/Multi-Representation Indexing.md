## Definition

- Combines [[proposition indexing]] and [[multi-vector retriever]]

## Process

1. Use an LLM to produce document summaries (propositions)
2. Embed summaries and store the embeddings in a vector store
3. Store the original documents in a byte store
4. Retrieve the corresponding document for the most relevant summary

## Code example

### Generate summaries

```python
docs = "..."  # some documents


import uuid
from langchain_core.documents import Document
from langchain_core.output_parsers import StrOutputParser
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI

chain = (
	{"doc": lambda x: x.page_content}
	| ChatPromptTemplate.from_template(
		"Summarize the following document:\n\n{doc}"
	)
	| ChatOpenAI(model="gpt-3.5-turbo",max_retries=0)
	| StrOutputParser()
)

summaries = chain.batch(docs, {"max_concurrency": 5})
```

### Store summaries and documents

```python
from langchain.storage import InMemoryByteStore
from langchain_openai import OpenAIEmbeddings
from langchain_community.vectorstores import Chroma
from langchain.retrievers.multi_vector import MultiVectorRetriever

# The vectorstore to use to index the child chunks

vectorstore = Chroma(
	collection_name="summaries",
	embedding_function=OpenAIEmbeddings()
)

# The storage layer for the parent documents

store = InMemoryByteStore()
id_key = "doc_id"

# The retriever

retriever = MultiVectorRetriever(
	vectorstore=vectorstore,
	byte_store=store,
	id_key=id_key,
)

doc_ids = [str(uuid.uuid4()) for _ in docs]

# Docs linked to summaries

summary_docs = [
	Document(page_content=s, metadata={id_key: doc_ids[i]})
	for i, s in enumerate(summaries)
]

# Add

retriever.vectorstore.add_documents(summary_docs)
retriever.docstore.mset(list(zip(doc_ids, docs)))
```

### Retrieval

```python
query = "Memory in agents"

sub_docs = vectorstore.similarity_search(query,k=1)
retrieved_docs = retriever.get_relevant_documents(query,n_results=1)
```
