## Components

- [[Thought]]: The LLM part of the agent decides what the next step should be
- [[Action]]: The agent takes an action, by calling the tools with the associated arguments
- [[Observation]]: The model reflects on the response from the tool

## Process

- The rules and guidelines are embedded directly into the system prompt
- The three components work together in a continuous loop
- Agents iterate through the loop until the objective is fulfilled

## Code examples

```python
system_message="""You are an AI assistant designed to help users efficiently and accurately. Your primary goal is to provide helpful, precise, and clear responses.

You have access to the following tools:
Tool Name: calculator, Description: Multiply two integers., Arguments: a: int, b: int, Outputs: int

You should think step by step in order to fulfill the objective with a reasoning divided into Thought/Action/Observation steps that can be repeated multiple times if needed.

You should first reflect on the current situation using `Thought: {your_thoughts}`, then (if necessary), call a tool with the proper JSON formatting `Action: {JSON_BLOB}`, or print your final answer starting with the prefix `Final Answer:`
"""
```
