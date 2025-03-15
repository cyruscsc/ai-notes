## Characteristics

- Start by fixing the values for evidence variables
- Sample the non-evidence variables using [[Conditional Probability|conditional probabilities]] in the [[Bayesian Network|Bayesian network]]
- Weight each sample by its likelihood: the probability of all the evidence occurring

## Example

> Using [[Bayesian Network#Example|example]] from Bayesian Networks for explanation

$$
P(Rain=light|Train=on time)
$$

1. Fix `Train` to be `on time`
2. Sample other variables based on their [[probability distribution]] given `on time`
3. Weight it by the conditional probability of the observed variable given its sampled parents
	- E.g. if we sampled `(light, yes, on time, attend)`, then weight this sample by $P(Train=on time|light,yes)$