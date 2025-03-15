## Definition

$$
AX=\lambda X
$$

> $A$: the transformation matrix
> $X$: the eigenvector
> $\lambda$: the eigenvalue

- An eigenvector is a non-zero vector that, when a [[linear transformation]] is applied to it, changes only by a scalar factor
	- The direction of an eigenvector remains unchanged when the transformation is applied
	- It may only be stretched, compressed, or reversed
- An eigenvalue represents the factor by which the eigenvector is stretched or compressed when the linear transformation is applied

## Characteristics

- Eigenvalues and eigenvectors always come in pairs
- A square matrix of size $n\times n$ has $n$ eigenvalues (including repeats)
- If $A$ is [[Singular Systems|singular]] (has zero [[determinant]]), then 0 is one of its eigenvalues
- Eigenvectors corresponding to different eigenvalues are linearly independent

## Calculation

### Finding eigenvalues

$$
\det(A-\lambda I)=0
$$

> Characteristic polynomial equation
> $A$: the transformation matrix
> $\lambda$: the eigenvalue
> $I$: the [[identity matrix]]

### Finding eigenvectors

1. For each eigenvalue $\lambda$, substitute it into $AX=\lambda X$
2. Solve the system $(A-\lambda I)X=0$, where the non-zero solutions are the eigenvectors corresponding to that eigenvalue

## Example

Given a transformation matrix $A=\begin{bmatrix}2&1\\0&3\end{bmatrix}$

Apply the characteristic polynomial equation

$$
\begin{aligned}
\det(A-\lambda I)&=0\\
\det(\begin{bmatrix}2&1\\0&3\end{bmatrix}-\lambda\begin{bmatrix}1&0\\0&1\end{bmatrix})&=0\\
\det(\begin{bmatrix}2-\lambda&1\\0&3-\lambda\end{bmatrix})&=0\\
(2-\lambda)(3-\lambda)&=0\\
\\
\lambda_1=2&\quad\lambda_2=3
\end{aligned}
$$

For each eigenvalue $\lambda$, apply the equation $AX=\lambda X$

$$
\begin{gathered}
AX_1=\lambda_1 X_1\\
\begin{bmatrix}2&1\\0&3\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}_1=2\begin{bmatrix}x_1\\x_2\end{bmatrix}_1\\
\begin{cases}
2x_1+x_2=2x_1\\
3x_2=2x_2
\end{cases}\\
\begin{bmatrix}x_1\\x_2\end{bmatrix}_1=\begin{bmatrix}1\\0\end{bmatrix}
\end{gathered}
\qquad
\begin{gathered}
AX_2=\lambda_2 X_2\\
\begin{bmatrix}2&1\\0&3\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}_2=3\begin{bmatrix}x_1\\x_2\end{bmatrix}_2\\
\begin{cases}
2x_1+x_2=3x_1\\
3x_2=3x_2
\end{cases}\\
\begin{bmatrix}x_1\\x_2\end{bmatrix}_2=\begin{bmatrix}1\\1\end{bmatrix}
\end{gathered}
$$

> If $x_1$ or $x_2$ has infinite solutions, take one possible solution that can form unit vector

- First pair of eigenvalue and eigenvector is $2$ and $\begin{bmatrix}1\\0\end{bmatrix}$
- Second pair of eigenvalue and eigenvector is $3$ and $\begin{bmatrix}1\\1\end{bmatrix}$
