## Effective branching factor

$$
b^*=\frac{\text{total nodes expanded}}{\text{depth of solution tree}}
$$

- Measures the efficiency of a heuristic by comparing the number of nodes expanded by a search algorithm to that of a uniform tree with the same depth and solution cost
- Lower values indicate a more efficient heuristic

## Relaxation

- Simplifies constraints in the problem to create an easier version
- Allows for heuristic derivation
- E.g. in pathfinding, ignoring obstacles provides a relaxed problem where straight-line distance (Euclidean distance) can serve as a heuristic

## Domination

$$
\forall n\quad h_1(n)\ge h_2(n)
$$

- $h_1$ dominates $h_2$ if $h_1$ is greater than or equal to $h_2$ for all nodes $n$, and both are [[Heuristic Design#Admissible heuristic|admissible]]
- Using a dominating heuristic is preferable as it provides tighter estimates and reduces the search space
