---
aliases:
  - ColBERT
---

## Definition

- Provides more nuanced and precise document representations

## Process

1. Tokenize texts using BERT’s Wordpiece tokenizer
2. Embed each token into a vector
3. Store the token-level embeddings
4. Tokenize query and generate token-level embeddings
5. Initial retrieval: Retrieve top `k` chunks with highest similarity to query tokens
6. Reranking: Sort the retrieved chunks based on aggregate similarity scores between query and document tokens

## Benefits

- Allows for more accurate matching, especially for specific or complex queries
- Captures more nuanced contextual information

## Code example

### Get Wikipedia page

```python
import requests

def get_wikipedia_page(title: str):
	"""
	Retrieve the full text content of a Wikipedia page.  
	:param title: str - Title of the Wikipedia page.
	:return: str - Full text content of the page as raw string.
	"""
	
	# Wikipedia API endpoint
	URL = "https://en.wikipedia.org/w/api.php"
	
	# Parameters for the API request
	params = {
		"action": "query",
		"format": "json",
		"titles": title,
		"prop": "extracts",
		"explaintext": True,
	}
	
	# Custom User-Agent header to comply with Wikipedia's best practices
	headers = {"User-Agent": "RAGatouille_tutorial/0.0.1 (ben@clavie.eu)"}
	
	response = requests.get(URL, params=params, headers=headers)
	data = response.json()
	
	# Extracting page content
	page = next(iter(data["query"]["pages"].values()))
	return page["extract"] if "extract" in page else None

full_document = get_wikipedia_page("Hayao_Miyazaki")
```

### Run RAG

```python
from ragatouille import RAGPretrainedModel

RAG = RAGPretrainedModel.from_pretrained("colbert-ir/colbertv2.0")

RAG.index(
	collection=[full_document],
	index_name="Miyazaki-123",
	max_document_length=180,
	split_documents=True,
)

# built-in search

results = RAG.search(
	query="What animation studio did Miyazaki found?",
	k=3
)

# as langchain retriever

retriever = RAG.as_langchain_retriever(k=3)
retriever.invoke("What animation studio did Miyazaki found?")
```
