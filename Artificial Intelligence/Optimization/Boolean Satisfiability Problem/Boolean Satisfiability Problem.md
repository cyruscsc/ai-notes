---
aliases:
  - SAT
---

## Definition

- Asks whether there exists an assignment of truth values to the variables of a given Boolean formula such that the formula evaluates to `true`
- Finds model that satisfies a formula, or to prove that there is no such model

## Algorithms

- [[DPLL]]
- [[WalkSAT]]

## Characteristics

- Problems are expressed as Boolean formulas with binary variables
- A subset of [[Constraint Satisfaction|CSP]] where the domain of each variable is `{true, false}`, and the constraints are logical formulas

## Approach

### Complete algorithms

- Guarantee finding a solution or proving unsatisfiability
- E.g. [[DPLL]], CDCL, [[WalkSAT]]

### Heuristic methods

- Approximate solutions with [[heuristic]] for large instances 
- E.g. [[local search]], [[genetic algorithm]]

## Related concepts

- [[Satisfiability]]
- [[NP-Complete]]

## Applications

- Product configuration
- Hardware verification
- Software verification
- Planning
- Scheduling
- Proofs in mathematics

