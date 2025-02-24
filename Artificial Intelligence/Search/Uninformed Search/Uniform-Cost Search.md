---
aliases:
  - UCS
---

## Characteristics

- A generalization of [[Breadth-First Search|BFS]] where path costs are not necessarily equal
- The frontier is a priority queue
- Expands the node with the lowest path cost
- Goal test is applied when the node is selected for expansion to avoid selecting a sub-optimal path
- Add test is added in case a better path is found to a node that is currently in the frontier

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: complete if $b$ is finite and all step costs $\le\epsilon$ for positive $\epsilon$
- [[Search Evaluation#Optimality|Optimality]]: optimal when a node is selected for expansion, the optimal path to the node has been found
- [[Search Evaluation#Time complexity|Time complexity]]: $O(b^{1+\lfloor\frac{C*}{\epsilon}\rfloor})$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(b^{1+\lfloor\frac{C*}{\epsilon}\rfloor})$

> $b$: branching factor
> $\epsilon$: positive value
> $C*$: cost of the optimal solution
