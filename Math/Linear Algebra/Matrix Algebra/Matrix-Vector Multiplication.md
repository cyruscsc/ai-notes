## Definition

$$
\begin{bmatrix}
a_{11}&a_{12}&a_{13}\\
a_{21}&a_{22}&a_{23}\\
a_{31}&a_{32}&a_{33}
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2\\x_3
\end{bmatrix}
=
\begin{bmatrix}
a_{11}x_1+a_{12}x_2+a_{13}x_3\\
a_{21}x_1+a_{22}x_2+a_{23}x_3\\
a_{31}x_1+a_{32}x_2+a_{33}x_3
\end{bmatrix}
$$

- Given a matrix $A\in\mathbb{R}^{m\times n}$ and a vector $x\in\mathbb{R}^n$
- The matrix-vector product $Ax$ results in a new vector $y\in\mathbb{R}^m$
- Where $y_i=\sum_{j=1}^{n}a_{ij}x_j$ for $i=1,2,\dots,m$

## Characteristics

- All [[dot product]] between each row of the matrix and the column vector stacked together
- Number of columns in matrix must equal length of vector
- Number of rows in matrix equals length of product vector