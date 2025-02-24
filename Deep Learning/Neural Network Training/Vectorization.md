## Matrix multiplication

### Transpose

- Flipped version of original matrix

$$
\begin{aligned}
\vec{a}=\begin{bmatrix}1\\2\end{bmatrix}\qquad
\vec{a}^T=\begin{bmatrix}1&2\end{bmatrix}\qquad
\vec{w}&=\begin{bmatrix}3\\4\end{bmatrix}
\end{aligned}
$$

### Dot product

- Takes two equal-length sequences of numbers and returns single number

$$
\begin{aligned}
\vec{a}\cdot\vec{w}=\vec{a}^T\vec{w}&=\sum_{i=1}^n{a_ib_i}\\
&=(1\times3)+(2\times4)\\
&=11
\end{aligned}
$$

### Vector matrix multiplication

$$
\begin{gathered}
\begin{aligned}
\vec{a}^T=\begin{bmatrix}1&2\end{bmatrix}\qquad
W=\begin{bmatrix}3&5\\4&6\end{bmatrix}\\
\end{aligned}\\
\begin{aligned}
Z&=\vec{a}^TW\\
&=\begin{bmatrix}\vec{a}^T\vec{w}_1&\vec{a}^T\vec{w}_2\end{bmatrix}\\
&=\begin{bmatrix}(1\times3)+(2\times4)&(1\times5)+(2\times6)\end{bmatrix}\\
&=\begin{bmatrix}11&17\end{bmatrix}
\end{aligned}
\end{gathered}
$$

### Matrix matrix multiplication

$$
\begin{gathered}
\begin{aligned}
\vec{a}^T=\begin{bmatrix}1&2\\-1&-2\end{bmatrix}\qquad
W=\begin{bmatrix}3&5\\4&6\end{bmatrix}\\
\end{aligned}\\
\begin{aligned}
Z&=\vec{a}^TW\\
&=\begin{bmatrix}
\vec{a}^T_1\vec{w}_1&\vec{a}^T_1\vec{w}_2\\
\vec{a}^T_2\vec{w}_1&\vec{a}^T_2\vec{w}_2
\end{bmatrix}\\
&=\begin{bmatrix}
(1\times3)+(2\times4)&(1\times5)+(2\times6)\\
(-1\times3)+(-2\times4)&(-1\times5)+(-2\times6)
\end{bmatrix}\\
&=\begin{bmatrix}
11&17\\
-11&-17
\end{bmatrix}
\end{aligned}
\end{gathered}
$$

## Matrix multiplication rules

- `num_col` of $M_1$ = `num_row` of $M_2$
- `num_row` of $M_{output}$ = `num_row` of $M_1$
- `num_col` of $M_{output}$ = `num_col` of $M_2$

## Code examples

### NumPy matrix multiplication

```python
import numpy as np

A = np.array([
  [1, -1, 0.1],
  [2, -2, 0.2]
])
AT = A.T # transpose
W = np.array([
  [3, 5, 7, 9],
  [4, 6, 8, 0]
])
Z = np.matmul(AT, W)
Z = AT @ W # alternative syntax
```

### Vectorized dense layer

```python
import nupmy as np

def dense(AT, W, b):
  '''
  Args:
    AT (ndarray (1,n))
    W  (ndarray (n,m))
    b  (ndarray (1,m))
  Returns:
    a_out (ndarray (1,m))
  '''
  z = np.matmul(AT, W) + b
  a_out = g(z)
  return a_out
```
