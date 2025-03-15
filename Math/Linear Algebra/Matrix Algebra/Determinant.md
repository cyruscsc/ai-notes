## Definition

$$
\begin{aligned}
|\begin{bmatrix}
a&b\\
c&d
\end{bmatrix}|
&=ad-bc
\\
\\
|\begin{bmatrix}
a&b&c\\
d&e&f\\
g&h&i
\end{bmatrix}|
&=aei+bfg+cdh-ceg-fha-ibd
\end{aligned}
$$

- Determinant = products of main diagonals - products of anti-diagonals

## Characteristics

### Matrix multiplication compatibility

$$
\det(AB)=\det(A)\det(B)
$$

- If $A$ and $B$ are square matrices of the same size
- If any of $A$ and $B$ is singular, $AB$ is [[Singular Systems|singular]]

### Scaling factor of transformation

- **Area/volume scaling**: The absolute value of the determinant gives the factor by which areas/volumes are scaled in [[linear transformation]]
- **Orientation**: a positive determinant preserves orientation, while a negative determinant inverts it
- **Zero determinant**: if $det(A)=0$, the transformation reduces the dimension of the space, squishing it onto a line or point
    - [[Singular Systems|Singular]] transformation
    - Area of a line/point = 0

### Reciprocal relationship

$$
\begin{aligned}
AA^{-1}&=I\\
\det(AA^{-1})&=\det(I)\\
\det(A)\det(A^{-1})&=1\\
\\\therefore
\det(A^{-1})&=\frac{1}{\det(A)}
\end{aligned}
$$

- The determinant of the [[Matrix Inverse|inverse]] is the reciprocal of the determinant of the original matrix
- This property only applies to invertible matrices