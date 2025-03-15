## Definition

- A search algorithm that maintains a single node and searches by moving to a neighbouring node
- Interested in finding the best answer to a question
- Interested only in the answer rather than the path to the answer as in [[search]]

## Characteristics

- Consider one node in a current state, then move the node to one of the current state’s neighbours
- Often brings to an answer that is not optimal but "good enough", conserving computational power

## Types of searches

- [[Hill Climbing]]
- [[Simulated Annealing]]
- [[Genetic Algorithm]]
- [[Tabu Search]]

## Concepts

### Objective function

- A function that we use to maximize the value of the solution

### Cost function

- A function that we use to minimize the cost of the solution

### Current state

- The state that is currently being considered by the function

### Neighbor state

- A state that the current state can transition to
- In a one-dimensional state-space landscape, a neighbor state is the state to either side of the current state
- Neighbor states are usually similar to the current state, and, therefore, their values are close to the value of the current state