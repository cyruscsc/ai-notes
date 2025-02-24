## Mean

$$
\mu=\frac{1}{m}\sum_{i=1}^mx^{(i)}
$$
> $m$: number of examples

## Variance

$$
\sigma^2=\frac{1}{m}\sum_{i=1}^m(x^{(i)}-\mu)^2
$$
> $m$: number of examples
> $\mu$: mean

## Standard deviation

$$
\sigma=\sqrt{\frac{1}{m}\sum_{i=1}^m(x^{(i)}-\mu)^2}
$$
> $m$: number of examples
> $\mu$: mean


## Code examples

### Estimate parameters for Gaussian distortion

```python
import numpy as np

def estimate_gaussian(X): 
  """
  Calculates mean and variance of all features in the dataset
  Args:
    X (ndarray)  : (m, n) Data matrix
  Returns:
    mu (ndarray) : (n,) Mean of all features
    var (ndarray): (n,) Variance of all features
  """
  m, n = X.shape
  mu = np.mean(X, axis=0)
  var = np.var(X, axis=0)
  return mu, var
```

### Compute probability density

```python
import numpy as np

def multivariate_gaussian(X, mu, var):
  """
  Computes the probability density function of the examples X under the multivariate gaussian distribution with parameters mu and var. If var is a matrix, it is treated as the covariance matrix. If var is a vector, it is treated as the var values of the variances in each dimension (a diagonal covariance matrix)
  """
  k = len(mu)
  if var.ndim == 1:
    var = np.diag(var)
  X = X - mu
  p = (2* np.pi)**(-k/2) * np.linalg.det(var)**(-0.5) * \
      np.exp(-0.5 * np.sum(np.matmul(X, np.linalg.pinv(var)) * X, axis=1))
  return p
```

### Select threshold

```python
import numpy as np

def select_threshold(y_val, p_val): 
  """
  Finds the best threshold to use for selecting outliers based on the results from a validation set (p_val) and the ground truth (y_val)
  Args:
    y_val (ndarray): Ground truth on validation set
    p_val (ndarray): Results on validation set
  Returns:
    epsilon (float): Threshold chosen 
    F1 (float)     : F1 score by choosing epsilon as threshold
  """ 
  best_epsilon = 0
  best_F1 = 0
  F1 = 0
  step_size = (max(p_val) - min(p_val)) / 1000
  for epsilon in np.arange(min(p_val), max(p_val), step_size):
    y_pred = p_val < epsilon
    tp = np.sum((y_pred == 1) & (y_val == 1))
    fp = np.sum((y_pred == 1) & (y_val == 0))
    fn = np.sum((y_pred == 0) & (y_val == 1))
    prec = tp / (tp + fp)
    rec = tp / (tp + fn)
    F1 = (2 * prec * rec) / (prec + rec)
    if F1 > best_F1:
      best_F1 = F1
      best_epsilon = epsilon
  return best_epsilon, best_F1
```

