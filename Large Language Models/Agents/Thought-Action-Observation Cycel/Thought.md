## Definition

- The agent's internal reasoning and planning process to solve the task

## Characteristics

- Utilizes the agent's LLM capacity to analyze information when presented in its prompt
- Breaks down complex problems into smaller, more manageable steps

## Types of Thoughts

- Planning
	- `I need to break this task into three steps: 1) gather data, 2) analyze trends, 3) generate report`
- Analysis
	- `Based on the error message, the issue appears to be with the database connection parameters`
- Decision making
	- `Given the user’s budget constraints, I should recommend the mid-tier option`
- Problem solving
	- `To optimize this code, I should first profile it to identify bottlenecks`
- Memory integration
	- `The user mentioned their preference for Python earlier, so I’ll provide examples in Python`
- Self-reflection
	- `My last approach didn’t work well, I should try a different strategy`
- Goal setting
	- `To complete this task, I need to first establish the acceptance criteria`
- Prioritization
	- `The security vulnerability should be addressed before adding new features`

## ReAct Approach

- ReAct is the concatenation of "reasoning" with "acting"
- A prompting technique that appends `Let's think step by step` before letting the LLM decode the next tokens
- Encourages the decoding process toward next tokens that generate a plan, rather than a final solution
- Encourages the model to decompose the problem into sub-tasks
