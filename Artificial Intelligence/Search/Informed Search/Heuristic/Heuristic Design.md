## Admissible heuristic

$$
\forall n\quad h(n)\le h^*(n)
$$

> $h^*(n)$: optimal cost to reach a goal from $n$

- Never overestimates the true cost to reach the goal from any node
- Guaranteed to find the optimal solution

## Consistent heuristic

$$
\forall n\quad h(n)\le c(n,p)+h(p)
$$

> $c(n,p)$: cost of moving from $n$ to $p$

- For every node $n$ and each successor $p$ of $n$, the estimated cost of reaching the goal from $n$ is no greater than the step cost of getting to $p$ plus the estimated cost of reaching the goal from $p$
- Consistency implies admissibility, forming a triangle inequality
- Aka monotonic heuristic