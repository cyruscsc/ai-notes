## Definition

$$
f'(x)=\frac{1}{x}
$$

> For $f(x)=\log(x)$

## Intuition

- As $g(y)=\log(y)$ is the inverse function of $f(x)=e^x$, so $g(y)=f^{-1}(y)$
- As the [[Derivatives of Inverse Functions|derivative of an inverse function]] is the inverse of the derivative of the original function, we have $g'(y)=\frac{1}{f'(x)}$
- Therefore:

$$
\begin{aligned}
g'(y)&=\frac{1}{f'(x)}\\
&=\frac{1}{f'(g(y))}\\
&=\frac{1}{e^{log(y)}}\\
&=\frac{1}{y}
\end{aligned}
$$

> $f'(x)=e^x$ for $f(x)=e^x$, see [[Derivative of Exponential Function]]
