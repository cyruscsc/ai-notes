## Definition

- The process of penalizing hypotheses that are more complex to favour simpler, more general hypotheses
- Used to avoid overfitting

## Topics

- [[Regularization Parameter]]

## Characteristics

$$
cost(h)=loss(h)+\lambda complexity(h)
$$

- Estimates the cost of the hypothesis function $h$ by adding up its loss and a measure of its complexity
- $\lambda$ is a constant that we can use to modulate how strongly to penalize for complexity in our cost function
	- The higher $\lambda$ is, the more costly complexity is