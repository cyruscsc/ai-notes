## Characteristics

- One technique of approximate inference
- Each variable is sampled for a value according to its [[Probability Distribution]]
- Can be inefficient when the evidence has a low probability
	- We may end up discarding many samples that do not match the evidence
	- Can get around with [[Likelihood Weighting]]

## Example

> Using [[Bayesian Network#Example|example]] from Bayesian Networks for explanation

### Unconditional probability

$$
P(Train=on time)
$$

1. Create samples by sampling each variable based on its probability distribution
	- `(light, no, on time, miss)`
	- `(light, yes, delayed, attend)`
	- `(none, no, on time, attend)`
	- and so on
2. Count the number of samples where `Train` is `on time`
3. Divide the result by the total number of samples

> See [[Unconditional Probability]]

### Conditional probability

$$
P(Rain=light|Train=ontime)
$$

1. Create samples by sampling each variable based on its probability distribution
	- `(light, no, on time, miss)`
	- `(light, yes, delayed, attend)`
	- `(none, no, on time, attend)`
	- and so on
2. Reject all samples where `Train` is not `on time`
3. Count the number of samples where `Rain` is `light`
4. Divide the result by the total number of samples where `Train` is `on time`

> See [[Conditional Probability]]

## Code examples

### Sampling function

```python
import pomegranate
from collections import Counter
from model import model

def generate_sample():
  # Mapping of random variable name to sample generated
  sample = {}

  # Mapping of distribution to sample generated
  parents = {}

  # Loop over all states, assuming topological order
  for state in model.states:

    # If we have a non-root node, sample conditional on parents
    if isinstance(state.distribution, pomegranate.ConditionalProbabilityTable):
      sample[state.name] = state.distribution.sample(parent_values=parents)
    # Otherwise, just sample from the distribution alone
    else:
      sample[state.name] = state.distribution.sample()

    # Keep track of the sampled value in the parents mapping
    parents[state.distribution] = sample[state.name]

  # Return generated sample
  return sample
```

### Computation

```python
# Rejection sampling
# Compute distribution of Appointment given that train is delayed
N = 10000
data = []

# Repeat sampling 10,000 times
for i in range(N):

  # Generate a sample based on the function that we defined earlier
  sample = generate_sample()

  # If, in this sample, the variable of Train has the value delayed, save the sample. Since we are interested interested in the probability distribution of Appointment given that the train is delayed, we discard the sampled where the train was on time.
  if sample["train"] == "delayed":
    data.append(sample["appointment"])

# Count how many times each value of the variable appeared. We can later normalize by dividing the results by the total number of saved samples to get the approximate probabilities of the variable that add up to 1.
print(Counter(data))
```
