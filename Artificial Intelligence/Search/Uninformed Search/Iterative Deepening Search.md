---
aliases:
  - IDS
---

## Characteristics

- An instance of [[Depth-First Search|DFS]] increasing the depth limit $l$ gradually until a goal is found
- Combines benefits of [[Breadth-First Search|BFS]] and DFS
- The preferred [[Uninformed Search]] approach when the search space is large and the depth of the solution is unknown

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: complete if $b$ is finite
- [[Search Evaluation#Optimality|Optimality]]: optimal if all actions have the same cost / path cost is a non-decreasing function of the depth of the node
- [[Search Evaluation#Time complexity|Time complexity]]: $O(b^d)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(bd)$

> $b$: branching factor
> $d$: depth of the shallowest solution
