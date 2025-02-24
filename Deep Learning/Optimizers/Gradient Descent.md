## Defintion

- An algorithm for minimizing loss when training neural networks

## Approach

- Start with a random choice of weights
	- This is our naive starting place, where we don’t know how much we should weight each input
- Repeat:
    - Calculate the gradient based on all data points that will lead to decreasing loss
    - Ultimately, the gradient is a vector (a sequence of numbers)
    - Update weights according to the gradient

## Characteristics

- Requires to calculate the gradient based on all data points
- Can be computationally costly
- Variants: [[Stochastic Gradient Descent]], [[Mini-Batch Gradient Descent]]

## Equation

$$
\begin{aligned}
&\text{Repeat until convergence}\\
&\begin{cases}
w_j&:=w_j-\alpha\frac{\partial}{\partial{w_j}}J(\vec{w},b)
&=w_j-\alpha[\frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})x_j^{(i)}]\\
b&:=b-\alpha\frac{\partial}{\partial{b}}J(\vec{w},b)
&=b-\alpha[\frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})]
\end{cases}\\
&\text{Simultaneously update }w_j,b
\end{aligned}
$$
> $w_j,b$: parameters
> $\alpha$: [[#Learning rate]]

- Goal: $\min\limits_{\vec{w},b}J(\vec{w},b)$
- Same equation for both [[Linear Regression|linear regression]] and [[Logistic Regression|logistic regression]], except different definitions of $f_{\vec{w},b}(\vec{x}^{(i)})$

## Intuition

- If slope of tangent at $(w,J(w,b))$ ...
  - $<0$, then $\frac{\partial}{\partial{w}}J(w,b)<0$, therefore $\text{new }w>\text{old }w$
  - $>0$, then $\frac{\partial}{\partial{w}}J(w,b)>0$, therefore $\text{new }w<\text{old }w$
- If slope of tangent at $(b,J(w,b))$ ...
  - $<0$, then $\frac{\partial}{\partial{b}}J(w,b)<0$, therefore $\text{new }b>\text{old }b$
  - $>0$, then $\frac{\partial}{\partial{b}}J(w,b)>0$, therefore $\text{new }b<\text{old }b$
- $J(w,b)$ is getting closer to the minimum for each time of repeating

## Learning rate

- Controls how big of a step
- If $\alpha$ is too small, gradient descent may be slow
- If $\alpha$ is too large, gradient descent may fail to converge and even diverge (overshoot)
- Derivative and update steps become smaller when getting closer to local minimum
- Can reach local minimum with fixed $\alpha$

### Learning curve graph

1. x-axis: number of iterations of gradient descent; y-axis: $J(\vec{w},b)$
2. With small enough $\alpha$, $J(\vec{w},b)$ should decrease on every iteration
3. If the curve has flattened out, declare convergence

### Automatic convergence test

1. Declare small $\epsilon$ (e.g. $10^{-3}$)
2. If $J(\vec{w},b)$ decreases by $\le\epsilon$ in one iteration, declare convergence

### Choosing learning rate

1. Try range of values of $\alpha$ (e.g. 0.001, 0.003, 0.01, 0.03, 0.1, 0.3, 1, ...)
2. Observe changes of learning curve to identify largest possible learning rate
3. Choose that learning rate or something slightly smaller than that

## Code examples

### NumPy

```python
import numpy as np

def zscore_normalize_features(X):
  """
  Compute X, zcore normalized by column
  Args:
    X (ndarray (m,n))     : input data, m examples, n features
  Returns:
    X_norm (ndarray (m,n)): input normalized by column
    mu (ndarray (n,))     : mean of each feature
    sigma (ndarray (n,))  : standard deviation of each feature
  """
  # find the mean of each column/feature
  mu = np.mean(X, axis=0) # mu will have shape (n,)
  # find the standard deviation of each column/feature
  sigma = np.std(X, axis=0) # sigma will have shape (n,)
  # element-wise, 
  # subtract mu for that column from each example, divide by std for that column
  X_norm = (X - mu) / sigma
  return (X_norm, mu, sigma)
```

### scikit-learn

```python
from sklearn.preprocessing import StandardScaler

# Perform z-score normalization
scaler = StandardScaler()
X_norm = scaler.fit_transform(X_train)
```

## Alternative

### Normal equation

- Only for linear regression
- Solve for $w,b$ without iterations
- Does not generalize to other learning algorithms
- Slow when number of features is large
- May be used in machine learning libraries that implement linear regression
