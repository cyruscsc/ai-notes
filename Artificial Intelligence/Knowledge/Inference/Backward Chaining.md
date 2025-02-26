## Approach

- Goal-driven
- [[Depth-First Search|DFS]], focuses only on relevant facts
- Breaks goal into sub-goals
- Starts with a goal and works backward to determine if the goal can be satisfied by existing facts

## Evaluation

- Time complexity: $O(n)$
- Space complexity: can be much less than linear in the size of KB

## Example

### Goal

- $\forall x. T(J,x)\land B(J)$ John is the tallest boy in class

### Knowledge base

- $T(J,K)$: John is taller than Kim
- $B(J)$: John is a boy
- $G(K)$: Kim is a girl
- $C(J,K)$ John and Kim are in the same class
- $\forall x. (x\ne J)\rightarrow T(K,x)$: everyone except John is shorter than Kim

### Process

1. Assume the goal $\forall x. T(J,x)\land B(J)$
2. Sub-goal $\forall x. T(J,x)$ is true,  since $T(J,K)$ and $\forall x. (x\ne J)\rightarrow T(K,x)$
3. Sub-goal $\land B(J)$ is true
4. All sub-goals are satisfied, so the goal is proven true

## Applications

- Diagnosis
- Troubleshooting
