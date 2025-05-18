---
aliases:
  - HyDE
---

## Definition

- Generates hypothetical document embeddings that represent ideal documents to answer a given query

## Process

1. Use a large language model to generate fake documents based on the search query
2. Encode these fake documents into embeddings
3. Use vector similarity search to find the most similar document chunks in the knowledge base

## Benefits

- Effective in out-of-domain scenarios and highly technical topics, where traditional embedding models might struggle to capture specific semantic meanings

## Code example

### Document

```python
from langchain.prompts import ChatPromptTemplate 

# HyDE document genration

template = """Please write a scientific paper passage to answer the question
Question: {question}
Passage:"""

prompt_hyde = ChatPromptTemplate.from_template(template)


from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI

generate_docs_for_retrieval = (
	prompt_hyde
	| ChatOpenAI(temperature=0)
	| StrOutputParser()
)

question = "What is task decomposition for LLM agents?"

generate_docs_for_retrieval.invoke({"question":question})
```

### Retrieval

```python
retrieval_chain = (
	generate_docs_for_retrieval
	| retriever
)

retireved_docs = retrieval_chain.invoke({"question":question})
```

### Generation

```python
# RAG

template = """Answer the following question based on this context:
{context}
Question: {question}
"""

prompt = ChatPromptTemplate.from_template(template)

final_rag_chain = (
	prompt
	| llm
	| StrOutputParser()
)

final_rag_chain.invoke({"context":retireved_docs,"question":question})
```
