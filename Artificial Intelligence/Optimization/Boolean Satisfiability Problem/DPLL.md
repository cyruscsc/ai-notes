## Definition

- A backtracking-based search algorithm designed to determine the [[Satisfiability]] of [[Propositional Logic]] formulas in [[Conjunction Normal Form]]

## Characteristics

- Systematically explores possible truth assignments for variables in a formula to determine whether it is satisfiable (`SAT`) or unsatisfiable (`UNSAT`)
- Improves upon naive [[Backtracking Search|backtracking]] by incorporating **unit propagation** and **pure literal elimination**, which reduce the search space significantly

## Approach

### Base case

- If the formula contains an [[Inference by Resolution#Empty clause|empty clause]], return `UNSAT`
- If all clauses are satisfied, return `SAT`

### Unit propagation

- **Unit clause** = a clause with only one unassigned literal (**unit literal**)
	- E.g. $(\neg A\lor\neg B\lor\neg C)$ with assignment `{A: true, B: true}`
- To satisfy this clause, assign the necessary truth value to the literal
- Propagate this assignment by simplifying the formula
	- Remove all clauses containing the satisfied literal
	- Remove the negation of the literal from other clauses

### Pure literal elimination

- **Pure literal** = a variable that appears with only one polarity (either always positive or always negative) in the formula
- Assign a truth value to this literal to satisfy all clauses containing it, and remove these clauses from the formula

### Splitting Rule

- Choose an unassigned literal and recursively check both possible truth assignments
- This step divides the problem into two subproblems, effectively performing a [[Depth-First Search|DFS]]

## Evaluation

- Completeness: guaranteed to find a solution if one exists
- Time complexity: $O(2^n)$
- Space complexity: $O(n)$

## Pseudocode

```
DPLL(Φ):
  if Φ contains an empty clause:
    return false

  if Φ has no clauses left:
    return true

  for each unit clause l in Φ:
    Φ ← UNIT-PROPAGATE(l, Φ)

  for each pure literal l in Φ:
    Φ ← PURE-LITERAL-ASSIGN(l, Φ)

  l ← CHOOSE-UNASSIGNED-LITERAL(Φ)

  return DPLL(Φ ∧ l) or DPLL(Φ ∧ ¬l)
```

> `Φ`: [[Conjunction Normal Form|CNF]] formula
