## Definition

- Combines [[multi-query]] retrieval with rank fusion techniques

## Process

1. Generate multiple queries from the original input
2. Retrieve relevant information for each query
3. Rank retrieved documents using [[Reciprocal Rank Fusion|RRF]]
4. Consolidate results into a ranked list

## Benefits

- Enhances the quality and relevance of retrieved information
- Improves the overall performance of RAG systems

## Code example

### Prompt

```python
from langchain.prompts import ChatPromptTemplate

# RAG-Fusion: related

template = """You are a helpful assistant that generates multiple search queries based on a single input query. \n
Generate multiple search queries related to: {question} \n
Output (4 queries):"""

prompt_rag_fusion = ChatPromptTemplate.from_template(template)


from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI

generate_queries = (
	prompt_rag_fusion
	| ChatOpenAI(temperature=0)
	| StrOutputParser()
	| (lambda x: x.split("\n"))
)
```

### Retrieval

```python
from langchain.load import dumps, loads

def reciprocal_rank_fusion(results: list[list], k=60):
	""" Reciprocal_rank_fusion that takes multiple lists of ranked documents and an optional parameter k used in the RRF formula """
	# Initialize a dictionary to hold fused scores for each unique document
	fused_scores = {}
	# Iterate through each list of ranked documents
	for docs in results:
		# Iterate through each document in the list, with its rank (position in the list)
		for rank, doc in enumerate(docs):
			# Convert the document to a string format to use as a key (assumes documents can be serialized to JSON)
			doc_str = dumps(doc)
			# If the document is not yet in the fused_scores dictionary, add it with an initial score of 0
			if doc_str not in fused_scores:
				fused_scores[doc_str] = 0
			# Retrieve the current score of the document, if any
			previous_score = fused_scores[doc_str]
			# Update the score of the document using the RRF formula: 1 / (rank + k)
			fused_scores[doc_str] += 1 / (rank + k)

	# Sort the documents based on their fused scores in descending order to get the final reranked results
	reranked_results = [
		(loads(doc), score)
		for doc, score in sorted(
			fused_scores.items(),
			key=lambda x: x[1],
			reverse=True
		)
	]

	# Return the reranked results as a list of tuples, each containing the document and its fused score
	return reranked_results

retrieval_chain_rag_fusion = (
	generate_queries
	| retriever.map()
	| reciprocal_rank_fusion
)

docs = retrieval_chain_rag_fusion.invoke({"question": question})
```

### Generation

```python
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
		"context": retrieval_chain_rag_fusion,
		"question": itemgetter("question")
	}
	| prompt
	| llm
	| StrOutputParser()
)

final_rag_chain.invoke({"question":question})
```