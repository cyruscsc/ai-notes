---
aliases:
  - Softmax
---

## Definition

$$
\begin{gathered}
a_j=P(y=j\vert\vec{x})=\frac{e^{z_j}}{\sum_{k=1}^Ne^{z_k}}\\
a(x)=
\begin{bmatrix}
P(y=1\vert{x;w,b})\\
\vdots\\
P(y=N\vert{x;w,b})
\end{bmatrix}
=\frac{1}{\sum_{k=i}^Ne^{z_k}}
\begin{bmatrix}
e^{z_1}\\
\vdots\\
e^{z_N}
\end{bmatrix}
\end{gathered}
$$
> Note: $a_1+a_2+\ldots+a_N=1$

- Output a vector of multiple activation values
- Each activation value depends on all values of $z$ 

## Loss function

$$
\begin{aligned}
L(a_1,\ldots,a_N,y)&=
\begin{cases}
-\log{a_1}&\quad\text{if }y=1\\
&\vdots\\
-\log{a_N}&\quad\text{if }y=N\\
\end{cases}\\
L(a_j,y)&=-\log{a_j}\qquad\text{if }y=j
\end{aligned}
$$

## Cost function

$$
\begin{gathered}
J(\vec{w},b)=-\frac{1}{m}[\sum_{i=1}^m\sum_{j=1}^N1\{y^{(i)}==j\}\log\frac{e^{z^{(i)}_j}}{\sum_{k=1}^Ne^{z^{(i)}_k}}]\\
1\{y==n\}==
\begin{cases}
1,\quad\text{if }y==n\\
0,\quad\text{otherwise}
\end{cases}
\end{gathered}
$$

## Code examples

```python
import numpy as np

def softmax(z):  
  """
  Softmax converts a vector of values to a probability distribution
  Args:
    z (ndarray (N,))  : input data, N features
  Returns:
    a (ndarray (N,))  : softmax of z
  """    
  a = ( 1 / np.sum(np.exp(z)) ) * np.exp(z)
  return a
```
