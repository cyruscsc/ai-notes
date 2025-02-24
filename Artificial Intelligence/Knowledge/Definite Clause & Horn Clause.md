## Definite clause

Example:
$$
\neg P\lor Q
$$

- A disjunction of literals with exactly one positive literal


## Horn clause

Example:
$$
\neg P\lor\neg Q
$$

- A disjunction of literals with at most one (i.e. 0 or 1) positive literal
- A more general form that includes definite clauses
- Implies a superset of definite clauses
- Can be efficiently processed using [[Resolution]] and other automated reasoning techniques
- **Closed** under resolution: resolving two horn clauses results in a horn clause