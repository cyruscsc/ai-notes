---
aliases:
  - Lazy Learning
---

## Definition

- Stores training data and uses it directly for predictions without creating a generalized model

## Approach

- Stores all training instances in memory
- Compares new instances to stored ones using similarity measures
	- E.g. Euclidean distance
- Predicts outcomes based on the closest or most similar instances

## Advantages

- Adapts well to complex, non-linear relationships
- No need for explicit model training
- Easy to update with new data

## Disadvantages

- Computationally expensive for large datasets
- Sensitive to noisy or irrelevant features

## Examples

- [[k-Nearest-Neighbours Classification]]
- [[Support Vector Machines]]
