## Definition

- A boundary in the state space that encloses all states with f-cost less than or equal to the contour value

## Characteristics

- Can be used to indicate all nodes whose $f(n)$ is less than or equal to some pre-specified number
	- Eg. $f(n)\le400$
- [[A* Search]] expands all nodes for which $f(n)<C^*$
	- This is what makes it guaranteed to be optimal
- It may also expand some nodes on goal contour itself
	- I.e. for which $f(n)=C^*$, before selecting a goal node
- [[A* Search]] expands no nodes with $f(n)>C^*$
	- Those nodes / subtrees are pruned
	- This is what makes it optimally efficient

> $f(n)$: [[Heuristic]]
> $C^*$: cost of the optimal solution
