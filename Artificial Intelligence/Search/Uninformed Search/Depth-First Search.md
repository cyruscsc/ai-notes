---
aliases:
  - DFS
---

## Characteristics

- Always expands the deepest node in the frontier
- Exhausts each one direction before trying another direction
- Explores a node to full depth before moving to next node
- The frontier is managed as a stack data structure

## Evaluation

- [[Search Evaluation#Completeness|Completeness]]: 
	- [[Tree Search vs Graph Search#Tree search|Tree-search]] based: not complete due to loops
	- [[Tree Search vs Graph Search#Graph search|Graph-search]] based: complete for finite graph
- [[Search Evaluation#Optimality|Optimality]]: not optimal, as it does not guarantee the shortest path
- [[Search Evaluation#Time complexity|Time complexity]]: $O(V+E)$ or $O(b^h)$
- [[Search Evaluation#Space complexity|Space complexity]]: $O(h)$ or $O(bh)$

> $V$: number of vertices
> $E$: number of edges
> $b$: branching factor
> $h$: maximum depth

### Pros

- Best case: Takes the least possible time to get to a solution
	- "Lucks out" and always chooses the right path to the solution (by chance)

### Cons

- Worst case: Takes the longest possible time before reaching the solution
	- Explores every possible path before finding the solution
- It is possible that the found solution is not optimal

## Pseudocode

```
input: root, target
stack.push(root)
found = FALSE
while not found and not stack.isEmpty:
  node = stack.pop
  if node == target:
    found = TRUE
  stack.push(node.children)
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
	  # Save the newest node
	  node = self.frontier[-1]
	  # Save all other nodes
	  # i.e. removing the last node
	  self.frontier = self.frontier[:-1]
	  return node
```