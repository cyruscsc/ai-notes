## Definition

$$
P(x_1,\dots,x_n|C)=\prod_{i=1}^{n}P(x_i|C)
$$

- Use [[Bayes’ rules]] naively
- Assumes that features are conditionally independent

## Problem of zero probability

-  A particular feature or word does not appear in the training data for a given class
- May result in a zero probability for the entire class due to multiplication in the Naive Bayes formula
- Can be addressed by applying [[Laplace smoothing]]
