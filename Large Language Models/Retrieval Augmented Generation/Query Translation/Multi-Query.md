## Definition

- Breaks down the original query into multiple differently worded questions from various perspectives

## Benefits

- Increases the likelihood of retrieving relevant documents by expanding the search scope
- Improves retrieval reliability by addressing the query from multiple angles

## Code example

### Prompt

```python
from langchain.prompts import ChatPromptTemplate

# multi-query: different perspectives

template = """You are an AI language model assistant. Your task is to generate five different versions of the given user question to retrieve relevant documents from a vector database. By generating multiple perspectives on the user question, your goal is to help the user overcome some of the limitations of the distance-based similarity search.
Provide these alternative questions separated by newlines. Original question: {question}"""

prompt_perspectives = ChatPromptTemplate.from_template(template)


from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI

generate_queries = (
	prompt_perspectives
	| ChatOpenAI(temperature=0)
	| StrOutputParser()
	| (lambda x: x.split("\n"))
)
```

### Retrieval

```python
from langchain.load import dumps, loads

def get_unique_union(documents: list[list]):
	""" Unique union of retrieved docs """
	# flatten list of lists, and convert each document to string
	flattened_docs = [
		dumps(doc) for sublist in documents for doc in sublist
	]
	# get unique documents
	unique_docs = list(set(flattened_docs))
	# return
	return [loads(doc) for doc in unique_docs]

question = "What is task decomposition for LLM agents?"

retrieval_chain = (
	generate_queries
	| retriever.map()
	| get_unique_union
)

docs = retrieval_chain.invoke({"question":question})
```

### Generation

```python
from operator import itemgetter
from langchain_openai import ChatOpenAI
from langchain_core.runnables import RunnablePassthrough

# RAG

template = """Answer the following question based on this context:
{context}
Question: {question}
"""

prompt = ChatPromptTemplate.from_template(template)
llm = ChatOpenAI(temperature=0)

final_rag_chain = (
	{
		"context": retrieval_chain,
		"question": itemgetter("question")
	}
	| prompt
	| llm
	| StrOutputParser()
)

final_rag_chain.invoke({"question":question})
```
