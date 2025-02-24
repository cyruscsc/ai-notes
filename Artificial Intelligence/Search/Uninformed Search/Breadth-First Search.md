---
aliases:
  - BFS
---

## Characteristics

- Always expands the shallowest node in the frontier
- Follows multiple directions at the same time
- Takes one step in each possible direction before taking the second step in each direction
- Explores all nodes at same level before moving to next level
- The frontier is managed as a queue data structure

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: complete for unweighted graph
- [[Search Evaluation#Optimality|Optimality]]: optimal for unweighted graphs
- [[Search Evaluation#Time complexity|Time complexity]]: $O(V+E)$ or $O(b^d)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(V)$ or $O(b^d)$

> $V$: number of vertices
> $E$: number of edges
> $b$: branching factor
> $d$: depth of shallowest solution

### Pros

- Guaranteed to find the optimal solution

### Cons

- Worst case: takes the longest possible time to run
- Almost guaranteed to take longer than the minimal time to run

## Pseudocode

```
input: root, target
queue.push(root)
found = FALSE
while not found and not queue.isEmpty:
  node = queue.pop
  if node == target:
    found = TRUE
  queue.push(node.children)
return found
```

## Code examples

### Node

```python
class Node():
  def __init__(self, state, parent, action):
    self.state = state
    self.parent = parent
    self.action = action
```

### Frontier

```python
class StackFrontier():
  def __init__(self):
    self.frontier = []

  def add(self, node):
    self.frontier.append(node)

  def contains_state(self, state):
    return any(node.state == state for node in self.frontier)

  def empty(self):
    return len(self.frontier) == 0

  def remove(self):
    if self.empty():
      # No solution
      raise Exception("empty frontier")
    else:
	  # Save the oldest node
	  node = self.frontier[0]
	  # Save all other nodes
	  # i.e. removing the first node
	  self.frontier = self.frontier[1:]
	  return node
```