## Characteristics

- Expands node with lowest value of $g(n)+h(n)$
- Considers $g(n)$ and $h(n)$
	- $g(n)$ = Cost that was accrued until the current location
	- $h(n)$ = Estimated cost from the current location to the goal
- Prioritizes expanding those nodes with minimum costs
- Once $(g(n)+h(n))$ exceeds the estimated cost of some previous option, the algorithm will ditch the current path and go back to the previous option
- Prevents itself from going down a long, inefficient path that $h(n)$ erroneously marked as best
- Can be memory intensive as it keeps all generated nodes

## Heuristic function

$$
f(n)=g(n)+h(n)
$$
> $g(n)$: cost to reach node $n$
> $h(n)$: estimated cost to goal

- [[Heuristic Design#Admissible heuristic|Admissible]]
	- Never overestimating the true cost
- [[Heuristic Design#Consistent heuristic|Consistent]]
	- $h(n)\le h(n’) + c$
	- $h(n)$ is consistent if for every node $n$ and successor node $n’$ with step cost $c$

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: complete if $b$ is finite and all step costs $\le\epsilon$ for positive $\epsilon$
- [[Search Evaluation#Optimality|Optimality]]: 
	- Tree-search based: optimal if heuristic is admissible
	- Graph-search based: optimal if heuristic is consistent
- Optimally efficient:
	- If heuristic is consistent
	- No other optimal algorithm is guaranteed to expand fewer nodes
- [[Search Evaluation#Time complexity|Time complexity]]: $O(b^d)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(b^d)$

> $b$: branching factor
> $d$: depth of the shallowest solution

May require further investigation on time and space complexities as textbook explains differently

> Complexity results may depend on the assumption made about the state space.
> Consider a state space that is a tree with reversible actions, with a single goal, then the time complexity is $O(b^{ed})$.
> When the state space has many goal states, particularly near-optimal goal states, then the search process can be led astray from the optimal path and there is an extra cost proportional to the number of goals whose cost is within a factor $e$ of the optimal cost.
> In the graph-search based version, there can be exponentially many states with $f(n)<C^*$ even if the absolute error is bounded by a constant.
> Overall the complexity of A* search makes it impractical to insist on finding an optimal solution.
> - $b$: branching factor
> - $d$: depth of the shallowest solution
> - $e$: relative error of the heuristic
> - $C^*$: cost of the optimal solution