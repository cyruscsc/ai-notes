## Characteristics

- Early on, higher temperature: more likely to make random decisions and accept neighbours that are worse than current state
- Later on, lower temperature: less likely to make random decisions and accept neighbours that are worse than current state
- Allows the algorithm to change its state to a neighbour that’s worse than the current state, which is how it can escape from [[Local & Global Minima & Maxima|local optima]]

## Parameters

### Accepting bad solutions

$$
p=e^{\frac{-\Delta E}{T}}
$$
> $p$: acceptance probability
> $\Delta E$: change in cost
> $T$: current temperature

- Poorer neighbouring solutions has lower acceptance probability
- Acceptance probability of bad solutions decreases when
	- given neighbouring solution is worse, or
	- current temperature decreases

### Min and max temperatures

- Min temperature is usually 0 or any reasonable low values
- Max temperature can be set by running a few experiments
	- Too cold: not accepting sufficient bad moves
	- Too hot: risk of random walk

### Cooling

$$
0.5\lt\alpha\lt1
$$
> $\alpha$: cooling schedule

- Allow adequate number of iterations at each temperature
	- More iterations with large temperature drops
	- Less iterations with small temperature drops

### Equilibrium condition

- Explore predefined number of neighbours at each temperature before decreasing
- Condition can be static or dynamic

### Termination condition

- Algorithm can be stopped
	- after completing predefined number of iterations, or
	- when temperature reaches 0

## Applications

- Traveling salesman problem
	- A neighbor state might be seen as a state where two arrows swap places
	- Calculating every possible combination makes this problem computationally demanding
	- By using the simulated annealing algorithm, a good solution can be found for a lower computational cost

## Pseudocode

```
input: a, t_max, t_min, s_init
s = s_init
t = t_max
while t > t_min:
  while not term_criterion:
    s' = neighboring solution
    d_E = s'.cost - s.cost
    if d_E < 0:
      s = s'
    else:
      p = e * (-d_E / T)
      s = s' with p
  t = a * t
return s
```

or

```
SIMULATED-ANNEALING(problem, max):
  current = initial state of problem
  for t = 1 to max:
    T = TEMPERATURE(T)
	neighbor = random neighbor of current
	dE = how much better neighbor is than current
	if dE > 0:
	  current = neighbor
	with probability e^(dE/T) set current = neighbor
  return current
```

- `max`: the number of times it should repeat itself
- `TEMPERATURE()`: 
	- Returns a higher value in the early iterations (when `t` is low)
	- Returns a lower value in later iterations (when `t` is high)
- `e^(dE/T)`:
	- The worse the neighbour state, the less likely it is to be chosen
		- The more negative the $\Delta E$ is, the closer the resulting value to 0
	- The earlier the algorithm is in its process, the more likely it is to set a worse neighbor state as current state
		- The higher the $T$ is, the closer $\frac{\Delta E}{T}$ is to 0, making the probability closer to 1
