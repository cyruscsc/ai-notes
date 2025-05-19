## Simple processor

- Agent output has no impact on program flow
- `process_llm_output(llm_response)`

## Router

- Agent output determines basic control flow
- `if llm_decision(): path_a() else: path_b()`

## Tool caller

- Agent ouput determines function execution
- `run_function(llm_chosen_tool, llm_chosen args)`

## Multi-step agent

- Agent output controls iteration and program continuation
- `while llm_should_continue(): execute_next_step()`

## Multi-agent

- One agentic workflow can start another agentic workflow
- `if llm_trigger(): execute_agent()`
