## Types of probability

- [[Unconditional Probability]]
- [[Conditional Probability]]
- [[Joint Probability]]

## Related concepts

- [[Random Variable]]
- [[Probability Distribution]]
- [[Independence]]
- [[Bayes’ Rules]]
- [[Probability Rules]]
- [[Bayesian Network]]
- [[Inference by Enumeration]]

## Definition

- Uncertainty can be represented as a number of events and the likelihood, or probability, of each of them happening
- AI can use partial information to make educated guesses about the future
- To use this information, which affects the probability that the event occurs in the future, we rely on [[Conditional Probability]]


## Possible worlds

$$
P(\omega)
$$

- Every possible situation can be thought of as a world $\omega$
- E.g. rolling a die can result in six possible worlds
- Probability of a certain world: $P(\omega)$

## Axioms in probability

$$
0\le P(\omega)\le1
$$

- 0 is an impossible event
	- E.g. rolling a standard die and getting a 7
- 1 is an event that is certain to happen
	- rolling a standard die and getting a value less than 10
- The higher the value, the more likely the event is to happen

$$
\sum_{\omega\in\Omega}P(\omega)=1
$$

- The probabilities of every possible event, when summed together, are equal to 1