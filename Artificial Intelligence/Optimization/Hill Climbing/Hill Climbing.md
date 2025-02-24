## Characteristics

- A local search algorithm
- Continuously increases some overall value with each iteration
- Terminates when peak/maximum value is reached
- The neighbor states are compared to the current state
- If any of them is better, we change the current node from the current state to that neighbor state
- May end up in [[Local & Global Minima & Maxima|local minima and maxima]]
- Don’t always give the best possible solution, but they can often give a good enough solution in situations where considering every possible state is computationally infeasible

## Variants

- Designed to overcome the problem of being stuck in local minima and maxima
- No matter the strategy, each one still has the potential of ending up in local minima and maxima and no means to continue optimizing
- [[Simple Hill Climbing]]
- [[Steepest-Ascent Hill Climbing]]
	- Choose the highest-valued neighbour
- Stochastic
	- Choose randomly from higher-valued neighbours
	- Choose to go to any direction that improves over our value
- First-choice
	- Choose the first higher-valued neighbour
- Random-restart
	- Conduct hill climbing multiple times
	- Each time, start from a random state
- Local beam search
	- Choose the $k$ highest-valued neighbors

## Strategies

- [[Initialization]]
- [[Neighbourhood Operator]]

## Pseudocode

```
Hill-Climb(problem):
  current = initial state of problem
  repeat:
    neighbor = best valued neighbor of current
	if neighbor not better than current:
	  return current
	current = neighbor
```
