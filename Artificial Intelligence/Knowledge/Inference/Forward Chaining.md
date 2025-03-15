## Approach

- Data-driven
- [[Breadth-First Search|BFS]], goes through all known facts
- Starts with known facts and applies [[inference rules]] to derive new facts until a goal is reached

## Evaluation

- Sound and complete for [[horn clause]] based KB
- Time complexity: $O(n)$

## Example

### Rules

- $(P\land Q)\rightarrow R$
- $R\rightarrow S$

> $P$: `d` barks
> $Q$: `d` eats bones
> $R$: `d` is a dog
> $S$: `d` is black

### Facts

- $P$
- $Q$

> - `Tony` barks
> - `Tony` eats bones

### Process

1. $P\land Q$ is true, so $R$ is also true
2. $R$ is true, so $S$ is also true

> 1. `Tony` barks and `Tony` eats bones, so `Tony` is a dog
> 2. `Tony` is a dog, so `Tony` is black

## Applications

- Planning
- Diagnostics
- Dynamic systems
