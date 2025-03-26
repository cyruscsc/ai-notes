## Definition

- Prompts for abstraction before diving into specifics

## Process

1. **Abstraction**: Focus on high-level concepts or principles related to the question
2. **Reasoning**: Use the abstracted information to reason through the specifics

## Benefits

- Significant improvements in STEM, knowledge-based QA, and multi-hop reasoning tasks

## Code example

### Prompt

```python
from langchain_core.prompts import ChatPromptTemplate, FewShotChatMessagePromptTemplate

# Few Shot Examples

examples = [
	{
		"input": "Could the members of The Police perform lawful arrests?",
		"output": "what can the members of The Police do?",
	},
	{
		"input": "Jan Sindel’s was born in what country?",
		"output": "what is Jan Sindel’s personal history?",
	},
]

# We now transform these to example messages

example_prompt = ChatPromptTemplate.from_messages([
	("human", "{input}"),
	("ai", "{output}"),
])

few_shot_prompt = FewShotChatMessagePromptTemplate(
	example_prompt=example_prompt,
	examples=examples,
)

prompt = ChatPromptTemplate.from_messages([
	(
		"system",
		"""You are an expert at world knowledge. Your task is to step back and paraphrase a question to a more generic step-back question, which is easier to answer. Here are a few examples:""",
	),
	# Few shot examples
	few_shot_prompt,
	# New question
	("user", "{question}"),
])

generate_queries_step_back = (
	prompt
	| ChatOpenAI(temperature=0)
	| StrOutputParser()
)

question = "What is task decomposition for LLM agents?"

generate_queries_step_back.invoke({"question": question})
```

### Retrieval and generation

```python
# Response prompt

response_prompt_template = """You are an expert of world knowledge. I am going to ask you a question. Your response should be comprehensive and not contradicted with the following context if they are relevant. Otherwise, ignore them if they are not relevant.
# {normal_context}
# {step_back_context}
# Original Question: {question}
# Answer:"""

response_prompt = ChatPromptTemplate.from_template(response_prompt_template)

chain = (
	{
		# Retrieve context using the normal question
		"normal_context": RunnableLambda(lambda x: x["question"]) | retriever,
		# Retrieve context using the step-back question
		"step_back_context": generate_queries_step_back | retriever,
		# Pass on the question
		"question": lambda x: x["question"],
	}
	| response_prompt
	| ChatOpenAI(temperature=0)
	| StrOutputParser()
)

chain.invoke({"question": question})
```
