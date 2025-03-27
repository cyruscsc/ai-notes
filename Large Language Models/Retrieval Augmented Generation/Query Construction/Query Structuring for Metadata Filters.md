## Definition

- Extracts relevant information from natural language queries to create targeted filters

## Process

1. **Metadata extraction**: Analyzes the user’s query to identify key entities, attributes, or phrases
2. **Filter construction**: Formats the extracted metadata into a structured filter
3. **Integration with retrieval**: Combines the metadata filter with the vector search to narrow down the relevant documents
	- **Pre-filtering**: Apply the metadata filter before the vector search, which can be more accurate but may affect the efficiency of approximate nearest neighbour (ANN) algorithms
	- **Post-filtering**: Perform the vector search first, then apply the metadata filter, which is more straightforward but may risk incomplete results

## Code example

### Metadata filter

```python
import datetime
from typing import Literal, Optional, Tuple
from langchain_core.pydantic_v1 import BaseModel, Field

class TutorialSearch(BaseModel):
	"""Search over a database of tutorial videos about a software library."""
	content_search: str = Field(
		...,
		description="Similarity search query applied to video transcripts.",
	)
	title_search: str = Field(
		...,
		description="Alternate version of the content search query to apply to video titles. Should be succinct and only include key words that could be in a video title.",
	)
	min_view_count: Optional[int] = Field(
		None,
		description="Minimum view count filter, inclusive. Only use if explicitly specified.",
	)
	max_view_count: Optional[int] = Field(
		None,
		description="Maximum view count filter, exclusive. Only use if explicitly specified.",
	)
	earliest_publish_date: Optional[datetime.date] = Field(
		None,
		description="Earliest publish date filter, inclusive. Only use if explicitly specified.",
	)
	latest_publish_date: Optional[datetime.date] = Field(
		None,
		description="Latest publish date filter, exclusive. Only use if explicitly specified.",
	)
	min_length_sec: Optional[int] = Field(
		None,
		description="Minimum video length in seconds, inclusive. Only use if explicitly specified.",
	)
	max_length_sec: Optional[int] = Field(
		None,
		description="Maximum video length in seconds, exclusive. Only use if explicitly specified.",
	)

	def pretty_print(self) -> None:
		for field in self.__fields__:
			if getattr(self, field) is not None and getattr(self, field) != getattr(self.__fields__[field], "default", None):
				print(f"{field}: {getattr(self, field)}")
```

### Integration with prompt

```python
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI

system = """You are an expert at converting user questions into database queries. \
You have access to a database of tutorial videos about a software library for building LLM-powered applications. \
Given a question, return a database query optimized to retrieve the most relevant results.
If there are acronyms or words you are not familiar with, do not try to rephrase them."""

prompt = ChatPromptTemplate.from_messages([
	("system", system),
	("human", "{question}"),
])

llm = ChatOpenAI(model="gpt-3.5-turbo-0125", temperature=0)

structured_llm = llm.with_structured_output(TutorialSearch)

query_analyzer = prompt | structured_llm

# example

query_analyzer.invoke({
	"question": "how to use multi-modal models in an agent, only videos under 5 minutes"
}).pretty_print()
```
