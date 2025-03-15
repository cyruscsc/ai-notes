## Model function

$$
\begin{aligned}
f_{\vec{w},b}(\vec{x})&=g(\vec{w}\cdot\vec{x}+b)=\frac{1}{1+e^{-(\vec{w}\cdot\vec{x}+b)}}\\
&=P(y=1\vert\vec{x};\vec{w},b)
\end{aligned}
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $\vec{w}\cdot\vec{x}$: dot product $w_1x_1+w_2x_2+\cdots+w_nx_n$
> $b$: parameter
> $f_{\vec{w},b}(\vec{x})$: probability that class is 1

- Let threshold $T=0.5$, when $f_{\vec{w},b}(\vec{x})<0.5$, $\hat{y}=0$; when $f_{\vec{w},b}(\vec{x})\ge0.5$, $\hat{y}=1$

### Sigmoid logistic function
$$
\begin{aligned}
g(z)=\frac{1}{1+e^{-z}}\qquad0<g(z)<1
\end{aligned}
$$
> $\because$ When $z=0$, $g(z)=0.5$
> $\therefore$ Let threshold $T=0.5$, when $\vec{w}\cdot\vec{x}+b<0$, $\hat{y}=0$; when $\vec{w}\cdot\vec{x}+b\ge0$, $\hat{y}=1$

## Decision boundary
$$
\begin{aligned}
g(\vec{w}\cdot\vec{x}+b)&=T\\
\vec{w}\cdot\vec{x}+b&=\log{(\frac{T}{1-T})}
\end{aligned}
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $\vec{w}\cdot\vec{x}$: dot product $w_1x_1+w_2x_2+\cdots+w_nx_n$
> $b$: parameter

- Dividing line that separates different classes

**Example**

Let $\vec{x}=\begin{bmatrix}x_1&x_2\end{bmatrix}$, $\vec{w}=\begin{bmatrix}1&1\end{bmatrix}$, $b=-3$, $T=0.5$
$$
\begin{aligned}
g(x_1+x_2-3)&=0.5\\
x_1+x_2-3&=0\\
x_1+x_2&=3
\end{aligned}
$$

- Decision boundary is $x_1+x_2=3$

## Cost function

$$
\begin{aligned}
J(\vec{w},b)
&=\frac{1}{m}\sum_{i=1}^mL(f_{\vec{w},b}(\vec{x}^{(i)}),y^{(i)})\\
&=-\frac{1}{m}\sum_{i=1}^m[y^{(i)}\log(f_{\vec{w},b}(\vec{x}^{(i)}))+(1-y^{(i)})\log(1-f_{\vec{w},b}(\vec{x}^{(i)}))]
\end{aligned}
$$
> $\vec{x}$: vector of input features $\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}$
> $\vec{w}$: vector of parameters $\begin{bmatrix}w_1&w_2&\cdots&w_n\end{bmatrix}$
> $b$: parameter

- Derived from statistics using [[Maximum Likelihood Estimation|MLE]]
- Also known as **binary cross entropy**
- To minimize cost function $J(\vec{w},b)$, see [[gradient descent]]

### Logistic loss function
$$
\begin{aligned}
L(f_{\vec{w},b}(\vec{x}^{(i)}),y^{(i)})&=
\begin{cases}
-\log(f_{\vec{w},b}(\vec{x}^{(i)}))&\text{if }y^{(i)}=1\\
-\log(1-f_{\vec{w},b}(\vec{x}^{(i)}))&\text{if }y^{(i)}=0
\end{cases}\\
&=-y^{(i)}\log(f_{\vec{w},b}(\vec{x}^{(i)}))-(1-y^{(i)})\log(1-f_{\vec{w},b}(\vec{x}^{(i)}))
\end{aligned}
$$

## Code examples

### NumPy

```python
import copy
import numpy as np

def compute_cost_logistic(X, y, w, b):
  """
  Computes cost
  Args:
    X (ndarray (m,n)): Data, m examples with n features
    y (ndarray (m,)) : target values
    w (ndarray (n,)) : model parameters  
    b (scalar)       : model parameter
  Returns:
    cost (scalar): cost
  """
  m = X.shape[0]
  cost = 0.0
  for i in range(m):
    z_i = np.dot(X[i], w) + b
    f_wb_i = sigmoid(z_i)
    cost +=  -y[i] * np.log(f_wb_i) - (1 - y[i]) * np.log(1 - f_wb_i)
  cost = cost / m
  return cost

def compute_gradient_logistic(X, y, w, b): 
  """
  Computes the gradient for logistic regression 
  Args:
    X (ndarray (m,n): Data, m examples with n features
    y (ndarray (m,)): target values
    w (ndarray (n,)): model parameters  
    b (scalar)      : model parameter
  Returns:
    dj_dw (ndarray (n,)): The gradient of the cost w.r.t. the parameters w
    dj_db (scalar)      : The gradient of the cost w.r.t. the parameter b
  """
  m,n = X.shape
  dj_dw = np.zeros((n,)) # (n,)
  dj_db = 0.
  for i in range(m):
    f_wb_i = sigmoid(np.dot(X[i], w) + b) # (n,)(n,) = scalar
    err_i  = f_wb_i  - y[i] # scalar
    for j in range(n):
      dj_dw[j] = dj_dw[j] + err_i * X[i,j] # scalar
    dj_db = dj_db + err_i
  dj_dw = dj_dw / m # (n,)
  dj_db = dj_db / m # scalar
  return dj_db, dj_dw

def gradient_descent(X, y, w_in, b_in, alpha, num_iters): 
  """
  Performs batch gradient descent
  Args:
    X (ndarray (m,n)   : Data, m examples with n features
    y (ndarray (m,))   : target values
    w_in (ndarray (n,)): Initial values of model parameters  
    b_in (scalar)      : Initial values of model parameter
    alpha (float)      : Learning rate
    num_iters (scalar) : number of iterations to run gradient descent
  Returns:
    w (ndarray (n,))   : Updated values of parameters
    b (scalar)         : Updated value of parameter 
  """
  w = copy.deepcopy(w_in) # avoid modifying global w within function
  b = b_in
  for i in range(num_iters):
    # Calculate the gradient and update the parameters
    dj_db, dj_dw = compute_gradient_logistic(X, y, w, b)   
    # Update Parameters using w, b, alpha and gradient
    w = w - alpha * dj_dw               
    b = b - alpha * dj_db               
  return w, b

def sigmoid(z):
  """
  Compute the sigmoid of z
  Args:
    z (array_like): A scalar or numpy array of any size
  Returns:
    g (array_like): sigmoid(z)
"""
  z = np.clip(z, -500, 500) # protect against overflow
  g = 1.0 / (1.0 + np.exp(-z))
  return g

def predict(X, w, b):
  """
  Performs prediction
  Args:
    x (ndarray): Shape (n,) example with multiple features
    w (ndarray): Shape (n,) model parameters
    b (scalar) : model parameter
  Returns:
    p (scalar) : prediction
  """
  p = sigmoid(X @ w + b)
  return p
```

### scikit-learn

```python
from sklearn.linear_model import LogisticRegression

# Create and fit the regression model
lr_model = LogisticRegression()
lr_model.fit(X, y)
# Make prediction
y_pred = lr_model.predict(X)
# Calculate accuracy
score = lr_model.score(X, y)
```
