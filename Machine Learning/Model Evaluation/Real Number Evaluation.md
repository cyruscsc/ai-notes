## Datasets

- Assume there are some labeled data (normal and anomalous examples)
- Training set (assumes normal examples)
- Validation set (includes most normal and a few anomalous examples)
- Test set (includes most normal and a few anomalous examples)

## Procedure

1. Fit model $p(x)$ on training set
2. Tune threshold $\epsilon$ and features $x_j$ on validation set
3. Evaluate model performance on test set

> $p(x)$: probability of $x$ being in a dataset $\{x^{(1)},\ldots,x^{(m)}\}$
> $\epsilon$: threshold of anomalies