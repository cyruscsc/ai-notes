## Reducing prediction errors

- Get more training examples $\rightarrow$ fixes high variance
- Use smaller sets of features $\rightarrow$ fixes high variance
- Get additional features $\rightarrow$ fixes high bias
- Add polynomial features ($x_1^2,x_2^2,x_1x_2,\text{etc}$) $\rightarrow$ fixes high bias
- Decrease $\lambda$ $\rightarrow$ fixes high bias
- Increase $\lambda$ $\rightarrow$ fixes high variance

## Diagnostic

- Gain insight into what is/isn't working within a learning algorithm
- Gain guidance into improving a learning algorithm's performance
- Can be a very good use of time

## Adding polynomial features

- Create non-straight line model to improve performance

### Code examples

```python
from sklearn.preprocessing import StandardScaler, PolynomialFeatures

# Create additional features
# Instantiate the class to make polynomial features
poly = PolynomialFeatures(degree=2, include_bias=False)
# Compute the number of features and transform the training set
X_train_mapped = poly.fit_transform(x_train)

# Scale input data
# Instantiate the class
scaler_poly = StandardScaler()
# Compute the mean and standard deviation of the training set then transform it
X_train_mapped_scaled = scaler_poly.fit_transform(X_train_mapped)
```
