---
aliases:
  - Adam
---


## Definition

- Also known as Adam algorithm
- Works much faster than [[Gradient Descent]]
- Standard and safe choice of optimization algorithm

## Intuition

- Use different learning rate for every single parameter of model
  - e.g. use $\alpha_1,\ldots,\alpha_{11}$ for $w_1,\ldots,w_{10},b$
- If $w_j$ (or $b$) keeps moving in same direction, increase $\alpha_j$
- If $w_j$ (or $b$) keeps oscillating, reduce $\alpha_j$

## Code examples

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.losses import SparseCategoricalCrossentropy
from tensorflow.keras.optimizers import Adam

model = Sequential([
  Dense(units=25, activation="sigmoid"),
  Dense(untis=15, activation="sigmoid"),
  Dense(units=10, activation="linear")
])
model.compile(
  optimizer=Adam(learning_rate=1e-3),
  loss=SparseCategoricalCrossentropy(from_logits=True)
)
model.fit(X, y, epochs=100)
```
