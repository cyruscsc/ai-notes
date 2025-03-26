## Definition

- Combines [[Least-to-Most Prompting|LtM]] and [[Iterative Retrieval Chain-of-Thought|IR-CoT]] to dynamically retrieve to aid in solving the subproblems

## Code example

### Prompt

```python
from langchain.prompts import ChatPromptTemplate

# decomposition

template = """You are a helpful assistant that generates multiple sub-questions related to an input question. \n
The goal is to break down the input into a set of sub-problems / sub-questions that can be answers in isolation. \n
Generate multiple search queries related to: {question} \n
Output (3 queries):"""

prompt_decomposition = ChatPromptTemplate.from_template(template)


from langchain_openai import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser

llm = ChatOpenAI(temperature=0)

generate_queries_decomposition = (
	prompt_decomposition
	| llm
	| StrOutputParser()
	| (lambda x: x.split("\n"))
)

question = "What are the main components of an LLM-powered autonomous agent system?"

questions = generate_queries_decomposition.invoke({"question":question})
```

### Recursive retrieval and generation

```python
from langchain.prompts import ChatPromptTemplate

template = """Here is the question you need to answer:
\n --- \n {question} \n --- \n
Here is any available background question + answer pairs:
\n --- \n {q_a_pairs} \n --- \n
Here is additional context relevant to the question:
\n --- \n {context} \n --- \n
Use the above context and any background question + answer pairs to answer the question: \n {question}
"""

decomposition_prompt = ChatPromptTemplate.from_template(template)


from operator import itemgetter
from langchain_core.output_parsers import StrOutputParser

def format_qa_pair(question, answer):
	"""Format Q and A pair"""
	formatted_string = ""
	formatted_string += f"Question: {question}\nAnswer: {answer}\n\n"
	return formatted_string.strip()

llm = ChatOpenAI(temperature=0)

q_a_pairs = ""

for q in questions:
	rag_chain = (
		{
			"context": itemgetter("question")| retriever,
			"question": itemgetter("question"),	
			"q_a_pairs": itemgetter("q_a_pairs")
		}
		| decomposition_prompt
		| llm
		| StrOutputParser()
	)
	
	answer = rag_chain.invoke({"question":q,"q_a_pairs":q_a_pairs})
	q_a_pair = format_qa_pair(q,answer)
	q_a_pairs = q_a_pairs + "\n---\n"+ q_a_pair
```

### Parallel retrieval and generation

```python
from langchain import hub
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.runnables import RunnablePassthrough, RunnableLambda
from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI

prompt_rag = hub.pull("rlm/rag-prompt")

def retrieve_and_rag(question, prompt_rag, sub_question_generator_chain):
	"""RAG on each sub-question"""
	# Use our decomposition
	sub_questions = sub_question_generator_chain.invoke({"question":question})
	# Initialize a list to hold RAG chain results
	rag_results = []
	
	for sub_question in sub_questions:
		# Retrieve documents for each sub-question
		retrieved_docs = retriever.get_relevant_documents(sub_question)
		# Use retrieved documents and sub-question in RAG chain
		answer = (
			prompt_rag
			| llm
			| StrOutputParser()
		).invoke({
			"context": retrieved_docs,
			"question": sub_question
		})
		rag_results.append(answer)
	
	return rag_results,sub_questions

# Wrap the retrieval and RAG process in a RunnableLambda for integration into a chain

answers, questions = retrieve_and_rag(question, prompt_rag, generate_queries_decomposition)

def format_qa_pairs(questions, answers):
	"""Format Q and A pairs"""
	formatted_string = ""
	for i, (question, answer) in enumerate(zip(questions, answers), start=1):
		formatted_string += f"Question {i}: {question}\nAnswer {i}: {answer}\n\n"
	return formatted_string.strip()

context = format_qa_pairs(questions, answers)

template = """Here is a set of Q+A pairs:
{context}
Use these to synthesize an answer to the question: {question}
"""

prompt = ChatPromptTemplate.from_template(template)

final_rag_chain = (
	prompt
	| llm
	| StrOutputParser()
)

final_rag_chain.invoke({"context":context,"question":question})
```
