---
aliases:
  - GBFS
---

## Characteristics

- Selects locally optimal solution at each stage to traverse through problem space
- Expands the node that is the closest to the goal
	- As determined by a [[Heuristic]] function $h(n)$
	- Better solutions may be found by exploring other nodes
- Look at distance between node `n` and target
	- Does not take into account the cost of travelling from node `n-1` to node `n`

## Heuristic function

$$
f(n)=h(n)
$$
> $h(n)$: cost of getting from node `n` to target

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]:
	- [[Tree Search vs Graph Search#Tree search|Tree-search]]based: not complete even in finite spaces due to the possibility of infinite loops
	- [[Tree Search vs Graph Search#Graph search|Graph-search]] based: complete in finite spaces
- [[Search Evaluation#Optimality|Optimality]]: non-optimal as it may not find the optimal path if intermediate steps do not have the lowest $f(n)$
- [[Search Evaluation#Time complexity|Time complexity]]: $O(b^d)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(b^d)$

> $b$: branching factor
> $d$: depth of the shallowest solution


## Pseudocode

```
input: root, target
node = root
found = FALSE
while node:
  candidate = node.bestChild
  if candidate == target:
    found = TRUE
    return found
  node = candidate
return found
```
