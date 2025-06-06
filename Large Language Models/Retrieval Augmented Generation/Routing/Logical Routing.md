## Definition

- Uses a set of predetermined criteria to decide how to handle a query without considering the user’s intent

## Code example

```python
from typing import Literal
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.pydantic_v1 import BaseModel, Field
from langchain_openai import ChatOpenAI

# Data model

class RouteQuery(BaseModel):
	"""Route a user query to the most relevant datasource."""
	datasource: Literal["python_docs", "js_docs", "golang_docs"] = Field(
		...,
		description="Given a user question choose which datasource would be most relevant for answering their question",
	)

# LLM with function call

llm = ChatOpenAI(model="gpt-3.5-turbo-0125", temperature=0)
structured_llm = llm.with_structured_output(RouteQuery)

# Prompt

system = """You are an expert at routing a user question to the appropriate data source.
Based on the programming language the question is referring to, route it to the relevant data source."""

prompt = ChatPromptTemplate.from_messages([
	("system", system),
	("human", "{question}"),
])

# Define router

router = prompt | structured_llm

# Route a query

question = """Why doesn't the following code work:
from langchain_core.prompts import ChatPromptTemplate
prompt = ChatPromptTemplate.from_messages(["human", "speak in {language}"])
prompt.invoke("french")
"""

result = router.invoke({"question": question})

def choose_route(result):
	if "python_docs" in result.datasource.lower():
		### Logic here
		return "chain for python_docs"
	elif "js_docs" in result.datasource.lower():
		### Logic here
		return "chain for js_docs"
	else:
		### Logic here
		return "golang_docs"


from langchain_core.runnables import RunnableLambda

full_chain = router | RunnableLambda(choose_route)
```
