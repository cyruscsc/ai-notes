---
aliases:
  - PCA
---

## Characteristics

- Find new axes and coordinates to reduce to number of features
- Commonly used for visualization (high dimensional to 2D or 3D)

## Algorithm

1. Preprocess features
	- [[Mean Normalization|Normalize]] data to have zero mean
	- Apply [[Feature Scaling|feature scaling]]
2. Find principal component $z$
	- The axis with maximum variance of data projection
	- Capture most information from data
3. Coordinate on new axis $z$
	$$
	z=u\cdot\hat{v}
	$$
    > $z$: distance from origin
     > $u$: vector of original data coordinates
     > $\hat{v}$: unit vector
     > Example: $\begin{bmatrix}2\\3\end{bmatrix}\cdot\begin{bmatrix}0.71\\0.71\end{bmatrix}=3.55$

## More principal components (PCs)

- $1^{st}$ principal component $z_1$
- $2^{nd}$ principal component $z_2$
- $3^{rd}$ principal component $z_3$
- A PC is always perpendicular to the previous PC(s)
	- $2^{nd}$ PC is at $90\degree$ to $1^{st}$ PC
	- $3^{rd}$ PC is at $90\degree$ to $1^{st}$ PC and $2^{nd}$ PC

## Approximation to original data

$$
u=z\times\hat{v}
$$
> $u$: vector of original data coordinates
> $z$: distance from origin
> $\hat{v}$: unit vector
> Example: $3.55\times\begin{bmatrix}0.71\\0.71\end{bmatrix}=\begin{bmatrix}0.52\\0.52\end{bmatrix}$

- **Reconstruction** = given $z$, find original $(x_1,x_2)$ (approximately)

## PCA vs linear regression

| Algorithm         |     Type     |   Axes    | Objective                        |
| :---------------- | :----------- | :-------: | :------------------------------- |
| Linear regression |  Supervised  |   $x,y$   | Minimize distance along $y$ axis |
| PCA               | Unsupervised | $x_1,x_2$ | Retain maximum variance          |

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
