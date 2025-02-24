## Characteristics

- Explores partial/complete neighbourhood at current state 
- Selects optimal solution from set of neighbours
- Guarantees to find a local optimum solution in short time
	- Can still get stuck in local optima

## Pseudocode

```
input: s_init
s = s_init
while not term_criterion:
  candidate = s.neighbor.all.explore
  if candidate.cost < s.cost:
    s = candidate
return s
```
