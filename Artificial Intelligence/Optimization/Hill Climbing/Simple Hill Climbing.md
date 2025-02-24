
### Characteristics

- Randomly explores possible next step
- Takes the step that is better than current state
- Guarantees to find a local optimum solution in short time
	- Can get stuck in local optima

### Pseudocode

```
input: s_init
s = s_init
while not term_criterion:
  candidate = s.neighbor.random.explore
  if candidate.cost < s.cost:
    s = candidate
return s
```
