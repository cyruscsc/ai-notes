## Model function

$$
f_{\vec{w},b}(\vec{x})=f(\vec{x})=\vec{w}\cdot\vec{x}+b\\
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $\vec{w}\cdot\vec{x}$: dot product $w_1x_1+w_2x_2+\cdots+w_nx_n$
> $b$: parameter

## Cost function

$$
J(\vec{w},b)=\frac{1}{2m}\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})^{2}=\frac{1}{2m}\sum_{i=1}^{m}(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})^{2}
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $b$: parameter

- Also known as **squared error cost function**
- To minimize cost function $J(\vec{w},b)$, see [[Gradient Descent]]

## Code examples

### NumPy

```python
import copy
import numpy as np

def compute_cost(X, y, w, b):
  """
  Compute cost
  Args:
    X (ndarray (m,n)): Data, m examples with n features
    y (ndarray (m,)) : target values
    w (ndarray (n,)) : model parameters
    b (scalar)       : model parameter
  Returns:
    cost (scalar)    : cost
  """
  m = X.shape[0]
  cost = 0.0
  for i in range(m):
    f_wb_i = np.dot(X[i], w) + b # (n,)(n,) = scalar (see np.dot)
    cost = cost + (f_wb_i - y[i]) ** 2 # scalar
    cost = cost / (2 * m) # scalar
  return cost

def compute_gradient(X, y, w, b):
  """
  Compute the gradient for linear regression
  Args:
    X (ndarray (m,n)): Data, m examples with n features
    y (ndarray (m,)) : target values
    w (ndarray (n,)) : model parameters
    b (scalar)       : model parameter
  Returns:
    dj_dw (ndarray (n,)): The gradient of the cost w.r.t. the parameters w
    dj_db (scalar)      : The gradient of the cost w.r.t. the parameter b
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
  return dj_db, dj_dw

def gradient_descent(X, y, w_in, b_in, cost_fn, gradient_fn, alpha, num_iters):
  """
  Perform batch gradient descent to learn w and b. Updates w and b by taking
  num_iters gradient steps with learning rate alpha
  Args:
    X (ndarray (m,n))  : Data, m examples with n features
    y (ndarray (m,))   : target values
    w_in (ndarray (n,)): initial model parameters
    b_in (scalar)      : initial model parameter
    cost_fn            : function to compute cost
    gradient_fn        : function to compute the gradient
    alpha (float)      : Learning rate
    num_iters (int)    : number of iterations to run gradient descent
  Returns:
    w (ndarray (n,))   : Updated values of parameters
    b (scalar)         : Updated value of parameter
  """
  w = copy.deepcopy(w_in) # avoid modifying global w within function
  b = b_in
  for i in range(num_iters):
    # Calculate the gradient and update the parameters
    dj_db, dj_dw = gradient_fn(X, y, w, b)
    # Update Parameters using w, b, alpha and gradient
    w = w - alpha * dj_dw
    b = b - alpha * dj_db
  return w, b

def predict(x, w, b):
  """
  Single predict using linear regression
  Args:
    x (ndarray): Shape (n,) example with multiple features
    w (ndarray): Shape (n,) model parameters
    b (scalar) : model parameter
  Returns:
    p (scalar) : prediction
  """
  p = X @ w + b
  return p
```

### scikit-learn

#### SGD method

- Performs best with normalized inputs

```python
from sklearn.linear_model import SGDRegressor

# Create and fit the regression model
sgdr = SGDRegressor(max_iter=1000)
sgdr.fit(X_norm, y_train)
# View gradient descent updates
num_completed_iters = sgdr.n_iter_
num_weight_updates = sgdr.t_
# View parameters
b_norm = sgdr.intercept_
w_norm = sgdr.coef_
# Make a prediction
y_pred = sgdr.predict(X_norm)
```

#### Closed-form method

- Does not require normalization

```python
from sklearn.linear_model import LinearRegression

# Create and fit the regression model
linear_model = LinearRegression()
linear_model.fit(X_train, y_train)
# View parameters
b = linear_model.intercept_
w = linear_model.coef_
# Make a prediction
y_pred = linear_model.predict(X_train)
```
