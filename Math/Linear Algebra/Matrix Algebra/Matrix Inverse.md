## Definition

$$
A\cdot A^{-1}=A^{-1}\cdot A=I
$$

- $A$: an invertible matrix
- $A^{-1}$: inverse of $A$
- $I$: [[identity matrix]]

- Multiplying the inverse of a matrix is multiplied with the original matrix results in the [[identity matrix]]

## Conditions for invertibility

A matrix $A$ is invertible ([[Non-Singular Systems|non-singular]]) if:

- It is a square matrix
- Its [[determinant]] $|A|\ne0$

## Formula

### General

$$
A^{-1}=\frac{1}{|A|}adj(A)
$$

> $|A|$: determinant of $A$
> $adj(A)$: adjugate (adjoint) of $A$, which is the transpose of its cofactor matrix

### For a 2x2 matrix

$$
\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}
$$

> $ad-bc$: determinant of the matrix