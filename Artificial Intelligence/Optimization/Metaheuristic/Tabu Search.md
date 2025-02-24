## Characteristics

- Maintains short-term memory (a finite list of moves)
	- To avoid exploring previously explored paths
- Tabu moves are allowed only under aspiration criteria
	- e.g. candidate solution is better than the best solution obtained

## Concepts

### Tabu tenure

- Duration of time a solution is prohibited from being revisited
- Best result can be obtained by incorporating medium-term memory and long-term memory

### Medium-term memory

- Aka intensification or exploitation
- Intended to bias the search towards promising areas of search space
	- Identify the most promising regions (features) in the best solutions
	- Intensify the search around those regions
- e.g. start with the best solution and focusing on the most promising features derived through the recent memory

### Long-term memory

- Aka diversification
- Promotes diversity in search process
- e.g. 

## Pseudocode

```
input: s_init
s = s_init
candidate = s_init
tabu_list = []
while not term_criterion:
  n_s = candidate.neigbor.all.explore
  s' = n_s.best.satisfy_tabu_list_and_asp_criteria
  if s'.cost < s.cost:
    s = s'
  tabu_list.push(candidate)
  candidate = s'
return s
```

