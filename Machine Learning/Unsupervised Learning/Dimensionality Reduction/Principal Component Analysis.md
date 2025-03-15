---
aliases:
  - PCA
---

## Definition

- A [[dimensionality reduction]] technique that transforms a high-dimensional dataset into a lower-dimensional space while preserving as much information as possible

## Process

### Step 1: data centering

$$
X_c=X-\bar{x}
$$

> $X_c$: centered matrix
> $X\in\mathbb{R}^{m\times n}$: a matrix with $m$ observations and $n$ variables
> $\bar{x}$: vector of mean of each variable

### Step 2: covariance matrix computation

$$
\begin{aligned}
C&=\frac{1}{m-1}(X-\bar{x})^T(X-\bar{x})\\
&=\frac{1}{m-1}(X_c)^T(X_c)
\end{aligned}
$$

- Covariance matrix $C$ is calculated to identify correlations between variables
- For dataset $X$ with $n$ variables, $C\in\mathbb{R}^{n\times n}$ is a $n\times n$ symmetric matrix
- Where $c_{ij}=\frac{1}{m-1}\sum_{k=1}^m(x_{ki}-\bar{x}_i)(x_{kj}-\bar{x}_j)$
- Every covariance matrix is symmetric, so the eigenvectors are always orthogonal

### Step 3: eigenvector and eigenvalue computation

- Solve $\det(C-\lambda I)=0$ to get the eigenvalue(s) $\lambda$
- For each [[Eigenvalue and Eigenvector|eigenvalue]], solve $(C-\lambda I)v=0$ to get the corresponding [[Eigenvalue and Eigenvector|eigenvector]] $v$

### Step 4: principal component selection

- Sort the eigenvectors in descending order of their corresponding eigenvalues
- The $k$ eigenvectors with the largest eigenvalues are selected as the principal components
- Where $k$ is the desired number of dimensions in the reduced space

### Step 5: data projection

$$
T=X_cV
$$

> $V$: the matrix of selected eigenvectors

- Project the original data onto the new subspace defined by the selected principal components

## Characteristics

- **Variance maximization**:
	- The first principal component maximizes the variance of the projected data
	- Each subsequent component maximizes the remaining variance while being orthogonal to all previous components
- **Orthogonality**
	- Principal components are orthogonal to each other
	- Their [[dot product]] is zero
- **Linear combinations**: each principal component is a linear combination of the original variables
- **Eigenvalue interpretation**: the eigenvalue $\lambda_i$ associated with the $i^{th}$ principal component represents the amount of variance explained by that component

## Example

Given a dataset $X=\begin{bmatrix}2&3\\3&6\\4&8\\5&11\end{bmatrix}$ with 4 observations and 2 features

Apply data centering, we have  $X_c=\begin{bmatrix}2&3\\3&6\\4&8\\5&11\end{bmatrix}-\begin{bmatrix}3.5\\7\end{bmatrix}=\begin{bmatrix}-1.5&-4\\-0.5&-1\\0.5&1\\1.5&4\end{bmatrix}$

Covariance matrix $C=\frac{1}{4-1}\begin{bmatrix}-1.5&-0.5&0.5&1.5\\-4&-1&1&4\end{bmatrix}\begin{bmatrix}-1.5&-4\\-0.5&-1\\0.5&1\\1.5&4\end{bmatrix}=\begin{bmatrix}0.833&2.333\\2.333&7.333\end{bmatrix}$

Solve $\det(\begin{bmatrix}0.833&2.333\\2.333&7.333\end{bmatrix}-\lambda I)=0$, we have $\lambda_1=8$ and $\lambda_2=0.167$

Substitue $\lambda_1$ and $\lambda_2$ into $(C-\lambda I)v=0$, we have $v_1=\begin{bmatrix}0.303\\0.953\end{bmatrix}$ and $v_2=\begin{bmatrix}-0.953\\0.303\end{bmatrix}$

From $\lambda_1,v_1$ and $\lambda_2,v_2$, $\lambda_1,v_1$ is chosen because of the higher eigenvalue

To project data, compute $T=X_cV$ where $V=v_1=\begin{bmatrix}0.303\\0.953\end{bmatrix}$

## Code examples

```python
import numpy as np
from sklearn.decomposition import PCA

# Example data
X = np.array(
  [[ 99, -1], 
   [ 98, -1],
   [ 97, -2],
   [101,  1],
   [102,  1],
   [103,  2]]
)

# One principle component
pca_1 = PCA(n_components=1)
pca_1.fit(X)
X_trans_1 = pca_1.transform(X)
# Transform data back to its original space
X_reduced_1 = pca_1.inverse_transform(X_trans_1)

# Two principle component
pca_2 = PCA(n_components=2)
pca_2.fit(X)
X_trans_2 = pca_2.transform(X)
# Transform data back to its original space
X_reduced_2 = pca_2.inverse_transform(X_trans_2)
```
