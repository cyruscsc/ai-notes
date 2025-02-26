## Definition

- A stochastic [[Local Search]] algorithm used for solving [[Boolean Satisfiability Problem|SAT]]

## Characteristics

- Focuses on exploring the search space by flipping variable assignments in a probabilistic manner
- May revisit the same model multiple times due to loops
- Can solve certain highly complex inputs
- Cannot used to show unsatisfiability
- Complimentary to [[DPLL]]:
	- Some SAT instances that are difficult for DPLL may be easy for WalkSAT
	- Some SAT instances that are difficult for WalkSAT may be easy for DPLL

## Approach

### Initialization

- Starts with a random model
- The truth value of each symbol is assigned randomly

### Small iterative changes

- Randomly select an unsatisfied clause
- Choose a variable within this clause to flip based on one of two strategies:
	- With probability $p$, pick a variable randomly (random move)
	- With probability $(1-p)$, pick a variable that maximize the number of satisfied clauses (greedy move)

### Stopping criteria

- If satisfying assignment is found, or
- After a predefined maximum number of flips or iterations

## Evaluation

- Completeness: incomplete as it does not guarantee finding a solution

## Pseudocode

```
WALKSAT(Φ, max_flips, p):
  X ← Random initial truth assignment

  for i = 1 to max_flips do:
    if X satisfies Φ:
      return X

    C ← RANDOM-UNSATISFIED-CLAUSE(Φ, X)

    if RANDOM() < p:
      v ← RANDOM-VARIABLE(C)
    else:
      v ← MAXIMIZING-VARIABLE(C, X)

    FLIP-VARIABLE(X, v)

  return "UNSAT"
```

> `Φ`: [[Conjunction Normal Form|CNF]] formula
> `max_flips`: maximum number of variable flips
> `p`: noise parameter (probability of random walk)
