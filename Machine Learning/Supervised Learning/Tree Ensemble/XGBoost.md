
## Definition

- Extreme Gradient Boosting
- Open source implementation of boosted trees
- Fast efficient implementation
- Good choice of default splitting and stopping criteria
- Built-in regularization to prevent overfitting
- Highly competitive algorithm for machine learning competitions (e.g. Kaggle competitions)

## Modification to bagged decision tree

- Deliberate practice
- Similar to [[bagged decision tree]] on creating new training set
- But more likely to pick misclassified examples from previously trained trees, instead of picking from all examples with equal ($\frac1m$) probability
- Get the next [[decision tree]] to do well on those misclassified examples

## Code examples

### Classification

```python
from xgboost import XGBClassifier

model = XGBClassifier()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Regression

```python
from xgboost import XGBRegressor

model = XGBRegressor()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```
