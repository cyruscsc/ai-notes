## Definition

- Recommend items based on ratings of users who gave similar ratings

## Notation

$x^{(i)}$ = feature vector for movie $i$

$w^{(j)},b^{(j)}$ = parameter for user $j$

$y^{(i,j)}$ = rating given by user $j$ to movie $i$

$r(i,j)=1$ if user $j$ has rated movie $i$

$\lambda$ = regularization parameter

$n$ = number of features

$n_u$ = number of users

$n_m$ = number of movies

## Model function

$$
\begin{aligned}
\text{Regression:}
&&f_{w,b,x}(x)&=w^{(j)}\cdot{x}^{(i)}+b^{(j)}\\
\text{Classification:}
&&f_{w,b,x}(x)&=g(w^{(j)}\cdot{x}^{(i)}+b^{(j)})=\frac{1}{1+e^{-(w^{(j)}\cdot{x}^{(i)}+b^{(j)})}}
\end{aligned}
$$
> $g$: [[Logistic Regression#Sigmoid logistic function|sigmoid function]]

- Fit a different [[Linear Regression#Model function|regression model]] or [[Logistic Regression#Model function|classification model]] to each user
- For regression, the model performs better with [[Mean Centring]] or [[Mean Normalization]]

## Cost function

$$
\begin{aligned}
\text{Regression:}&&
J(w,b,x)&=\frac{1}{2}\sum_{(i,j):r(i,j)=1}(f(x)-y^{(i,j)})^2+\frac{\lambda}{2}\sum_{j=1}^{n_u}\sum_{k=1}^n(w^{(j)}_k)^2+\frac{\lambda}{2}\sum_{i=1}^{n_m}\sum_{k=1}^n(x^{(i)}_k)^2\\
\text{Classification:}&&
J(w,b,x)&=\sum_{(i,j):r(i,j)=1}L(f_{w,b,x}(x),y^{(i,j)})
\end{aligned}
$$
> $L$: loss function

### Breakdowns

$$
\begin{aligned}
J(w^{(j)},b^{(j)})&=\frac{1}{2}\sum_{i:r(i,j)=1}(f(x)-y^{(i,j)})^2+\frac{\lambda}{2}\sum_{k=1}^n(w^{(j)}_k)^2
&(1.1)\\
J(w^{(1)},b^{(1)},\ldots,w^{(n_u)},b^{(n_u)})&=\frac{1}{2}\sum_{j=1}^{n_u}\sum_{i:r(i,j)=1}(f(x)-y^{(i,j)})^2+\frac{\lambda}{2}\sum_{j=1}^{n_u}\sum_{k=1}^n(w^{(j)}_k)^2
&(1.2)\\
J(x^{(i)})&=\frac{1}{2}\sum_{j:r(i,j)=1}(f(x)-y^{(i,j)})^2+\frac{\lambda}{2}\sum_{k=1}^n(x^{(i)}_k)^2
&(2.1)\\
J(x^{(1)},\ldots,x^{(n_m)})&=\frac{1}{2}\sum_{i=1}^{n_m}\sum_{j:r(i,j)=1}(f(x)-y^{(i,j)})^2+\frac{\lambda}{2}\sum_{i=1}^{n_m}\sum_{k=1}^n(x^{(i)}_k)^2
&(2.2)
\end{aligned}
$$
> $(1.1)$: learn parameters $w^{(j)},b^{(j)}$ for single user
> $(1.2)$: learn parameters $w^{(1)},b^{(1)},\ldots,w^{(n_u)},b^{(n_u)}$ for all users
> $(2.1)$: learn feature $x^{(i)}$ for single movie
> $(2.2)$: learn feature $x^{(1)},\ldots,x^{(n_m)}$ for all movies

### Loss function

$$
L(f_{w,b,x}(x),y^{(i,j)})=-y^{(i,j)}\log{(f_{w,b,x}(x))-(1-y^{(i,j)})\log{(1-f_{w,b,x}(x))}}
$$

## Gradient descent

$$
\begin{aligned}
&\text{Repeat until convergence}\\
&\begin{cases}
w^{(j)}_i=w^{(j)}_i-\alpha\frac{\partial}{\partial{w}^{(j)}_i}J(w,b,x)\\
b^{(j)}=b^{(j)}-\alpha\frac{\partial}{\partial{b}^{(j)}}J(w,b,x)\\
x^{(i)}_k=x^{(i)}_k-\alpha\frac{\partial}{\partial{x}^{(i)}_k}J(w,b,x)
\end{cases}\\
&\text{Simultaneously update }w^{(j)}_i,b^{(j)},x^{(i)}_k
\end{aligned}
$$

## Finding related items

- Find item $k$ similar to item $i$ = find item $k$ with $\min\|x^{(k)}-x^{(i)}\|^2$ from item $i$
$$
\text{Squared distance }\|x^{(k)}-x^{(i)}\|^2=\sum_{l=1}^n(x^{(k)}_l-x^{(i)}_l)^2
$$

## Limitations

- Not good at **cold start problem**
	- Rank new items that few users have rated
	- Show something reasonable to new users who have rated few items
- No natural way to use side information about items or users
	- Item: genre, movie stars, studio, ...
	- User: demographics, expressed preferences, ...

## Code examples

### Cost function (loop)

```python
import numpy as np

def cofi_cost_func(X, W, b, Y, R, lambda_):
  """
  Returns the cost for the content-based filtering
  Args:
    X (ndarray (num_movies,num_features)): matrix of item features
    W (ndarray (num_users,num_features)) : matrix of user parameters
    b (ndarray (1, num_users)            : vector of user parameters
    Y (ndarray (num_movies,num_users)    : matrix of user ratings of movies
    R (ndarray (num_movies,num_users)    : matrix, where R(i, j) = 1 if the i-th movies was rated by the j-th user
  lambda_ (float): regularization parameter
  Returns:
    J (float) : Cost
  """
  nm, nu = Y.shape
  J = 0
  # Cost
  for j in range(nu):
    for i in range(nm):
      J += R[i,j] * (np.dot(W[j], X[i]) + b[0,j] - Y[i,j]) ** 2
  J /= 2
  # Regularization
  nf = X.shape[1]
  lambda_w = 0
  for j in range(nu):
    for k in range(nf):
      lambda_w += W[j,k] ** 2
  lambda_w = lambda_w * lambda_ / 2
  J += lambda_w
  lambda_x = 0
  for i in range(nm):
    for k in range(nf):
      lambda_x += X[i,k] ** 2
  lambda_x = lambda_x * lambda_ / 2
  J += lambda_x
  return J
```

### Cost function (vectorization)

```python
import tensorflow as tf

def cofi_cost_func_v(X, W, b, Y, R, lambda_):
  """
  Returns the cost for the content-based filtering
  Vectorized for speed. Uses tensorflow operations to be compatible with custom training loop.
  Args:
    X (ndarray (num_movies,num_features)): matrix of item features
    W (ndarray (num_users,num_features)) : matrix of user parameters
    b (ndarray (1, num_users)            : vector of user parameters
    Y (ndarray (num_movies,num_users)    : matrix of user ratings of movies
    R (ndarray (num_movies,num_users)    : matrix, where R(i, j) = 1 if the i-th movies was rated by the j-th user
    lambda_ (float): regularization parameter
  Returns:
    J (float) : Cost
  """
  j = (tf.linalg.matmul(X, tf.transpose(W)) + b - Y)*R
  J = 0.5 * tf.reduce_sum(j**2) + (lambda_/2) * (tf.reduce_sum(X**2) + tf.reduce_sum(W**2))
  return J
```

### Custom training loop

```python
import tensorflow as tf

# Set Initial Parameters (W, X), use tf.Variable to track these variables
tf.random.set_seed(1234) # for consistent results
W = tf.Variable(tf.random.normal((num_users, num_features),dtype=tf.float64), name='W')
X = tf.Variable(tf.random.normal((num_movies, num_features),dtype=tf.float64), name='X')
b = tf.Variable(tf.random.normal((1, num_users), dtype=tf.float64), name='b')
# Instantiate an optimizer
optimizer = keras.optimizers.Adam(learning_rate=1e-1)
# Train model
iterations = 200
lambda_ = 1
for iter in range(iterations):
  # Use TensorFlow’s GradientTape
  # to record the operations used to compute the cost 
  with tf.GradientTape() as tape:
    # Compute the cost (forward pass included in cost)
    cost_value = cofi_cost_func_v(X, W, b, Ynorm, R, lambda_)
  # Use the gradient tape to automatically retrieve
  # the gradients of the trainable variables with respect to the loss
  grads = tape.gradient(cost_value, [X, W, b])
  # Run one step of gradient descent by updating
  # the value of the variables to minimize the loss.
  optimizer.apply_gradients(zip(grads, [X, W, b]))
  # Log periodically.
  if iter % 20 == 0:
    print(f"Training loss at iteration {iter}: {cost_value:0.1f}")
```
