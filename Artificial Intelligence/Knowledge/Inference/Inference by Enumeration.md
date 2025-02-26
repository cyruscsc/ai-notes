## Definition

$$
P(X|e)=\alpha P(X,e)=\alpha\sum_{y\in Y}P(X,e,y)
$$

> $X$: query variable
> $e$: observed evidence
> $y$: all the values of the hidden variables $Y$
> $\alpha$: normalizes the result such that we end up with probabilities that [[Probability#Axioms in probability|add up to 1]]

- A process of finding the **[[Probability Distribution]]** of variable $X$ given observed evidence $e$ and some hidden variables $Y$
- Generalizes inference to probabilistic reasoning by summing probabilities over hidden variables $y\in Y$
- The probability distribution of $X$ given $e$ is equal to a normalized probability distribution of $X$ and $e$
	- Sum the normalized probability of $X$, $e$, and $y$
	- $y$ takes each time a different value of the hidden variables $Y$

## Characteristics

- Allows us to figure out the probability distributions for some values
- Does not allow us to know new information for certain
- Inefficient, especially when there are many variables in the model
- A different way would be abandoning **exact inference** in favor of [[Sampling|approximate inference]]
	- Lose some precision (often negligible) in the generated probabilities
	- Gain a scalable method of calculating probabilities

## Properties

> Using [[Bayesian Network#Example|example]] from Bayesian Networks for explanation

### Query X

- The variable for which we want to compute the probability distribution
- E.g. `Train`

### Evidence variables E

- One or more variables that have been observed for event $e$
- E.g. `Rain`, because we might have observed that there is light rain, and this observation helps us compute the probability that the train is delayed

### Hidden variables Y

- Variables that aren’t the query and also haven’t been observed
- E.g. `Maintenance`, because we can’t know if there is maintenance on the track further down the road, standing at the train station

### Goal

- Calculate $P(X|e)$
- E.g. compute the probability distribution of `Train` (the query) based on the evidence $e$ that we know there is light rain

## Example

> Using [[Bayesian Network#Example|example]] from Bayesian Networks for explanation
> Compute the probability distribution of the Appointment variable given the evidence that there is light rain and no track maintenance

- Query $X$: `Appointment`
- Evidence variables $E$:
	- $e_1$: `light` for `Rain`
	- $e_2$: `no` for `Maintenance`
- Hidden variables $Y$: `Train`
- Goal: calculate $P(Appointment|light,no)$

$$
\begin{aligned}
P(Appointment|light,no)&=\alpha P(Appointment,light,no)\\
&=\alpha[P(Appointment,light,no,delayed)+P(Appointment,light,no,on time)]
\end{aligned}
$$

- Express the possible values of the Appointment [[Random Variable]] as a proportion by rewriting with $\alpha$
	- See [[Joint Probability]]
- Use [[Marginalization]] to calculate $P(Appointment|light,no)$ by adding up the probabilities of all possible values (`on time` and `delayed`) of hidden variable `Train`

## Code examples

> Python's library: pomegranate

### Create nodes

```python
from pomegranate import *

# Rain node has no parents
rain = Node(DiscreteDistribution({
  "none": 0.7,
  "light": 0.2,
  "heavy": 0.1
}), name="rain")

# Track maintenance node is conditional on rain
maintenance = Node(ConditionalProbabilityTable([
  ["none", "yes", 0.4],
  ["none", "no", 0.6],
  ["light", "yes", 0.2],
  ["light", "no", 0.8],
  ["heavy", "yes", 0.1],
  ["heavy", "no", 0.9]
], [rain.distribution]), name="maintenance")

# Train node is conditional on rain and maintenance
train = Node(ConditionalProbabilityTable([
  ["none", "yes", "on time", 0.8],
  ["none", "yes", "delayed", 0.2],
  ["none", "no", "on time", 0.9],
  ["none", "no", "delayed", 0.1],
  ["light", "yes", "on time", 0.6],
  ["light", "yes", "delayed", 0.4],
  ["light", "no", "on time", 0.7],
  ["light", "no", "delayed", 0.3],
  ["heavy", "yes", "on time", 0.4],
  ["heavy", "yes", "delayed", 0.6],
  ["heavy", "no", "on time", 0.5],
  ["heavy", "no", "delayed", 0.5],
], [rain.distribution, maintenance.distribution]), name="train")

# Appointment node is conditional on train
appointment = Node(ConditionalProbabilityTable([
  ["on time", "attend", 0.9],
  ["on time", "miss", 0.1],
  ["delayed", "attend", 0.6],
  ["delayed", "miss", 0.4]
], [train.distribution]), name="appointment")
```

- Create the nodes
- Provide a probability distribution for each one

### Create model

```python
# Create a Bayesian Network and add states
model = BayesianNetwork()
model.add_states(rain, maintenance, train, appointment)

# Add edges connecting nodes
model.add_edge(rain, maintenance)
model.add_edge(rain, train)
model.add_edge(maintenance, train)
model.add_edge(train, appointment)

# Finalize model
model.bake()
```

- Create the model by adding all the nodes
- Describe which node is the parent of which other node by adding edges between them

> Recall that a [[Bayesian Network|Bayesian network]] is a directed graph, consisting of nodes with arrows between them

### Run model

```python
# Calculate probability for a given observation
probability = model.probability([["none", "no", "on time", "attend"]])

print(probability)
```

- Run the model with the values we are interested in
- E.g. what is the probability that there is no rain, no track maintenance, the train is on time, and we attend the meeting

### Provide probability distributions

```python
# Calculate predictions based on the evidence that the train was delayed
predictions = model.predict_proba({
  "train": "delayed"
})

# Print predictions for each node
for node, prediction in zip(model.states, predictions):
  if isinstance(prediction, str):
    print(f"{node.name}: {prediction}")
  else:
    print(f"{node.name}")
    for value, probability in prediction.parameters[0].items():
      print(f"    {value}: {probability:.4f}")
```

- Provide probability distributions for all variables given some observed evidence
- E.g. given that the train was delayed, compute the probability distributions of `Rain`, `Maintenance`, and `Appointment`
