---
aliases:
  - Back prop
---

## Definition

- Efficient way to compute derivatives of cost function (takes roughly $N+P$ steps for $N$ nodes and $P$ parameters)
- The main algorithm used for training neural networks with hidden layers

## Approach

- Calculate error for output layer
- For each layer, starting with output layer and moving inwards towards earliest hidden layer:
	- Propagate error back one layer. In other words, the current layer that’s being considered sends the errors to the preceding layer
	- Update weights

## Derivatives

- Rate of change of a function with respect to a variable
$$
\begin{gathered}
\text{If }w\uparrow\epsilon\text{ causes }J(w)\uparrow{k}\times\epsilon\text{ then}\\
\frac{\partial}{\partial{w}}J(w)=k
\end{gathered}
$$
> $\epsilon$: amount of increment

| $J(w)$ | $\frac{\partial}{\partial{w}}J(w)$ | If $J(2),{w}\uparrow0.001$ |
| :--: | :--: | :--- |
| $\frac1w$ | $\frac{-1}{w^2}$ | $J(w)=0.49975$ |
| $w$ | $1$ | $J(w)=2.001$ |
| $w^2$ | $2w$ | $J(w)=4.004001$ |
| $w^3$ | $3w^2$ | $J(w)=8.012006$ |

## Computational graph

- Simplifies the computation of complex derivatives by breaking them into smaller steps
- **Chain rule** = expresses the derivative of the composition of two differentiable functions
