## Definition

$$
P(b|a)=\frac{P(b)P(a|b)}{P(a)}
$$

- Commonly used in probability theory to compute [[conditional probability]]
- Knowing the conditional probability of a visible effect given an unknown cause, $P(visible effect|unknown cause)$, allows us to calculate the probability of the unknown cause given the visible effect, $P(unknown cause|visible effect)$

## Example

### Weather

> - 80% of rainy afternoons start with cloudy mornings $P(clouds|rain)$
> - 40% of days have cloudy mornings $P(clouds)$
> - 10% of days have rainy afternoons $P(rain)$

$$
\begin{aligned}
P(rain|clouds)&=\frac{P(rain)P(clouds|rain)}{P(clouds)}\\
&=\frac{(0.1)(0.8)}{(0.4)}\\
&=0.2
\end{aligned}
$$

- The probability that it rains in the afternoon given that it was cloudy in the morning is 20%

### Disease diagnosis

- We can learn $P(medical test results|disease)$ through medical trials
	-  Test people with the disease and see how often the test picks up on that
- Knowing this, we can calculate $P(disease|medical test results)$
