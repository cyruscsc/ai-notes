## Definition

- Regression with decision tree; predicting a number

## Choosing a split

- Reduce the variance instead of entropy of the values in each sub-branch
- Reduction in weighted average variance

$$
RV=\sigma^2(p_1^\text{root})-(w^\text{left}\sigma^2(p_1^\text{left})+w^\text{right}\sigma^2(p_1^\text{right}))
$$
> $\sigma^2$: variance
> $p_1$: fraction of true examples
> $w$: fraction of examples in sub-branch

## Learning process

1. Start will all examples at the root node
2. Calculate reduction in weighted average variance for all possible features
3. Split on the feature with the highest reduction in weighted average variance
4. Keep performing recursive splitting until stopping criteria is met

