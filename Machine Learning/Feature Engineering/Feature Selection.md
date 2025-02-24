
## Transforming non-gaussian feature

$$
\begin{aligned}
x&=\log{(x+c)},&&\text{where }c\ge0\\
x&=x^c,&&\text{where }0<c<1
\end{aligned}
$$

## Common problem in anomaly detection


- $p(x)$ is comparable for normal and anomalous examples (large for both)
  - $p(x)$ should be large ($\ge\epsilon$) for normal examples
  - $p(x)$ should be small ($<\epsilon$) for anomalous examples

> $p(x)$: probability of $x$ being in a dataset $\{x^{(1)},\ldots,x^{(m)}\}$
> $\epsilon$: threshold of anomalies


### Add new feature

1. Identify new feature that helps distinguish anomalous examples
2. Add this feature to the algorithm

### Create derived feature

1. Identify relationship of existing features that helps distinguish anomalous examples
2. Combine the related existing features to create derived feature
