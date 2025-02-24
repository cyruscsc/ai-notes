---
aliases:
  - Sigmoid
---

## Definition

$$
g(z)=P(y=1\vert\vec{x})=\frac{1}{1+e^{-z}}
$$
> $0<g(z)<1$

- Gives as output any real number from 0 to 1
- Expresses graded confidence in its judgment
- Slower computation and learning than [[Rectified Linear Unit|ReLU]]
- Goes flat in two places (left and right of graph)
	- Results in more places in cost function that are flat
	- Slows down gradient descent
