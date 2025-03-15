## Characteristics

- Runs two simultaneous searches
	- One forward from the initial state
	- One backward from the goal state
- Check whether the frontiers of he two searches intersect
- Helpful when there is only one goal state
- Difficult to use when the goal is an abstract description

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]:  complete if $b$ is finite and if both directions use [[Breadth-First Search|BFS]]
- [[Search Evaluation#Optimality|Optimality]]:  optimal if step costs are identical and both directions use BFS
- [[Search Evaluation#Time complexity|Time complexity]]:  $O(b^{\frac{d}{2}})$
- [[Search Evaluation#Space complexity|Space complexity]]:  $O(b^{\frac{d}{2}})$

> $b$: branching factor
> $d$: depth of the shallowest solution