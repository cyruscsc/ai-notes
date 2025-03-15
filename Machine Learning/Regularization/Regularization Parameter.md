## Selection procedure

1. Fit parameters by minimizing cost with different values of $\lambda$
2. Compute training error $J_{train}(\vec{w},b)$
3. Compute validation error $J_{cv}(\vec{w},b)$
4. Select $\lambda$ with lowest test error $J_{cv}(\vec{w}^{<d>},b^{<d>})$
5. Compute test error $J_{test}(\vec{w}^{<d>},b^{<d>})$
6. Report estimated generalization error $J_{test}(\vec{w}^{<d>},b^{<d>})$

## Cost function

$$
J(\vec{w},b)=\frac{1}{2m}[\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})^2+\frac{\lambda}{2m}\sum_{j=1}^nw_j^2]
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $b$: parameter
> $\lambda$: regularization parameter
> $n$: number of features

## Gradient descent

$$
\begin{aligned}
&\text{Repeat until convergence}\\
&\begin{cases}
w_j=w_j-\alpha\frac{\partial}{\partial{w_j}}J(\vec{w},b)=w_j-\alpha[\frac{1}{m}\sum_{i=1}^m[(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})x_j^{(i)}]+\frac{\lambda}{m}w_j]\\
b=b-\alpha\frac{\partial}{\partial{b}}J(\vec{w},b)=b-\alpha[\frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})]
\end{cases}\\
&\text{Simultaneously update }w_j,b
\end{aligned}
$$
> $w_j,b$: parameters
> $\alpha$: learning rate
> $\lambda$: regularization parameter

- Same equation for both [[Linear Regression|linear regression]] and [[Logistic Regression|logistic regression]], except different definitions of $f_{\vec{w},b}(\vec{x}^{(i)})$
- See [[gradient descent]]

## Code examples

### Linear regression

```python
import numpy as np

def compute_cost_linear_reg(X, y, w, b, lambda_=1):
  """
  Computes the cost over all examples
  Args:
    X (ndarray (m,n): Data, m examples with n features
    y (ndarray (m,)): target values
    w (ndarray (n,)): model parameters
    b (scalar)      : model parameter
    lambda_ (scalar): Controls amount of regularization
  Returns:
    total_cost (scalar): cost
  """
  m  = X.shape[0]
  n  = len(w)
  cost = 0.
  for i in range(m):
    f_wb_i = np.dot(X[i], w) + b # (n,)(n,) = scalar, see np.dot
    cost = cost + (f_wb_i - y[i]) ** 2 # scalar
  cost = cost / (2 * m) # scalar
  reg_cost = 0
  for j in range(n):
    reg_cost += (w[j]**2) # scalar
  reg_cost = (lambda_/(2*m)) * reg_cost # scalar
  total_cost = cost + reg_cost # scalar
  return total_cost # scalar

def compute_gradient_linear_reg(X, y, w, b, lambda_): 
    """
    Computes the gradient for linear regression 
    Args:
      X (ndarray (m,n): Data, m examples with n features
      y (ndarray (m,)): target values
      w (ndarray (n,)): model parameters
      b (scalar)      : model parameter
      lambda_ (scalar): Controls amount of regularization
    Returns:
      dj_dw (ndarray (n,)): The gradient of the cost w.r.t. the parameters w
      dj_db (scalar):       The gradient of the cost w.r.t. the parameter b
    """
    m,n = X.shape # (number of examples, number of features)
    dj_dw = np.zeros((n,))
    dj_db = 0.

    for i in range(m):
        err = (np.dot(X[i], w) + b) - y[i]
        for j in range(n):
            dj_dw[j] = dj_dw[j] + err * X[i, j]
        dj_db = dj_db + err
    dj_dw = dj_dw / m
    dj_db = dj_db / m
    for j in range(n):
      dj_dw[j] = dj_dw[j] + (lambda_ / m) * w[j]
    return dj_db, dj_dw
```

### Logistic regression

```python
import numpy as np

def compute_cost_logistic_reg(X, y, w, b, lambda_=1):
  """
  Computes the cost over all examples
  Args:
    X (ndarray (m,n): Data, m examples with n features
    y (ndarray (m,)): target values
    w (ndarray (n,)): model parameters
    b (scalar)      : model parameter
    lambda_ (scalar): Controls amount of regularization
  Returns:
    total_cost (scalar): cost
  """
  m,n  = X.shape
  cost = 0.
  for i in range(m):
    z_i = np.dot(X[i], w) + b # (n,)(n,) = scalar, see np.dot
    f_wb_i = sigmoid(z_i) # scalar
    cost += -y[i] * np.log(f_wb_i) - (1 - y[i]) * np.log(1-f_wb_i) # scalar
  cost = cost / m # scalar
  reg_cost = 0
  for j in range(n):
    reg_cost += (w[j] ** 2) # scalar
  reg_cost = (lambda_ / (2 * m)) * reg_cost # scalar
  total_cost = cost + reg_cost # scalar
  return total_cost # scalar

def compute_gradient_logistic_reg(X, y, w, b, lambda_): 
  """
  Computes the gradient for linear regression
  Args:
    X (ndarray (m,n): Data, m examples with n features
    y (ndarray (m,)): target values
    w (ndarray (n,)): model parameters
    b (scalar)      : model parameter
    lambda_ (scalar): Controls amount of regularization
  Returns
    dj_dw (ndarray Shape (n,)): The gradient of the cost w.r.t. the parameters w
    dj_db (scalar)            : The gradient of the cost w.r.t. the parameter b
  """
  m,n = X.shape
  dj_dw = np.zeros((n,)) # (n,)
  dj_db = 0.0 # scalar
  for i in range(m):
    f_wb_i = sigmoid(np.dot(X[i], w) + b) # (n,)(n,)=scalar
    err_i  = f_wb_i  - y[i] # scalar
    for j in range(n):
      dj_dw[j] = dj_dw[j] + err_i * X[i,j] # scalar
    dj_db = dj_db + err_i
  dj_dw = dj_dw / m # (n,)
  dj_db = dj_db / m # scalar
  for j in range(n):
    dj_dw[j] = dj_dw[j] + (lambda_ / m) * w[j]
  return dj_db, dj_dw
```
