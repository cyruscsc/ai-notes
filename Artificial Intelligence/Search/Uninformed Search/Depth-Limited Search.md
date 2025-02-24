---
aliases:
  - DLS
---

## Characteristics

- An instance of [[Depth-First Search|DFS]] incorporating a depth limit $l$
	- All nodes at depth $L$ are treated as if they have no successors
	- DFS can be seen as a special case with $l=\infty$
- Includes a recursive function that calls itself on each of its children
- Aims to overcome the failure of DFS in infinite state spaces by solving the infinite-path problem

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: incomplete if $l<d$
- [[Search Evaluation#Optimality|Optimality]]: Non-optimal if $l>d$
- [[Search Evaluation#Time complexity|Time complexity]]: $O(b^l)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(bl)$

> $b$: branching factor
> $d$: depth of the shallowest solution
> $l$: depth limit