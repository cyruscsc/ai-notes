## Definition

- The generated output lacks logical consistency or consistency with user-provided instructions and contextual information

## Instruction inconsistency

> Instruction:
> ```
> Translate the English question into Spanish: 
> "What is the capital of France?"
> ```
> Response:
> ```
> The capital of France is Paris.
> ```

- The generated output deviates from a user’s directive

## Context inconsistency

> Retrieved context:
> ```
> The Nile is a major north-flowing river in northeastern Africa. It’s traditionally considered the longest river in the world. Originating in the Great Lakes region of central Africa, it flows through several countries before emptying into the Mediterranean Sea.
> ```
> Instruction:
> ```
> Summarize the retrieval document above.
> ```
> Response:
> ```
> The Nile originates from the mountain ranges of central Africa and flows into the Mediterranean.
> ```

- The generated output is unfaithful with the user’s provided contextual information

## Logical inconsistency

> Instruction:
> ```
> Solve the equation 2x + 3 = 11 step by step.
> ```
> Response:
> ```
> Step 1: Subtract 3 from both sides to get: 2x = 8. 
> Step 2: Divide both sides by 2 to get: x = 3. 
> So the result of the equation is x=3.
> ```

- The generated outputs exhibit internal logical contradictions, often observed in reasoning tasks
- Manifests as inconsistency both among the reasoning steps themselves and between the steps and the final answer