## Definition

- An algorithm that evaluates whether the query $\alpha$ is true in every model where the knowledge base $KB$ is true
- Systematically evaluates all possible **binary truth value** assignments for the symbols in a knowledge base $KB$ and a query ($\alpha$)

## Approach

- Starts with an empty model (partial assignment of truth values)
- Recursively assign truth values to each symbol
- For each complete model:
	- Check if KB is true under the model
	- If KB is true, verify whether $\alpha$ is also true
- If $\alpha$ is true in all models where KB is true, return `true`; otherwise, return `false`

## Evaluation

- Soundness: if the algorithm says $KB\models\alpha$, it is guaranteed to be correct
- Completeness: it finds $KB\models\alpha$ if it is true for all models
- Time complexity: $O(2^n)$
- Space complexity: $O(n)$

> $n$: number of symbols

## Pseudocode

```
TT-ENTAILS?(KB, α):
  symbols = list of all symbols in KB and α
  return TT-CHECK-ALL(KB, α, symbols, {})

TT-CHECK-ALL(KB, α, symbols, model):
  if EMPTY(symbols):
    if PL-TRUE(KB, model):
      return PL-TRUE?(α, model)
    else:
      return True
  else:
    P = FIRST(symbols)
    rest = REST(symbols)
    return (TT-CHECK-ALL(KB, α, rest, EXTEND(P, True, model)) and
            TT-CHECK-ALL(KB, α, rest, EXTEND(P, False, model)))
```

> `PL-TRUE(q, m)`: checks if a sentence `q` is true under a given model `m`
> `EXTEND(p, v, m)` extends the model `m` by assigning `p = v`

- When KB is `false`, always return `true` as `α` is trivially entailed