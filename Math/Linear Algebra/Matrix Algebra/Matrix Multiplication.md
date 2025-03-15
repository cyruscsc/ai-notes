## Definition

$$
\begin{bmatrix}
a_{11}&a_{12}&a_{13}\\
a_{21}&a_{22}&a_{23}
\end{bmatrix}
\begin{bmatrix}
b_{11}&b_{12}\\
b_{21}&b_{22}\\
b_{31}&b_{32}
\end{bmatrix}=
\begin{bmatrix}
a_{11}b_{11}+a_{12}b_{21}+a_{13}b_{31}&a_{11}b_{12}+a_{12}b_{22}+a_{13}b_{32}\\
a_{21}b_{11}+a_{22}b_{21}+a_{23}b_{31}&a_{21}b_{12}+a_{22}b_{22}+a_{23}b_{32}\\
\end{bmatrix}
$$

- Given two matrices $A\in\mathbb{R}^{m\times n}$ and $B\in\mathbb{R}^{n\times p}$
- The matrix-matrix product $AB$ results in a new matrix $C\in\mathbb{R}^{m\times p}$
- Where $c_{ij}=\sum_{k=1}^na_{ik}b_{kj}$ for $i=1,2,\dots,m$ and $j=1,2,\dots,p$
- $c_{ij}$ is the [[dot product]] between the $i^{th}$ row of $A$ and the $j^{th}$ column of $B$

## Characteristics

- **Non-commutativity**: In general, $AB\ne BA$, even when both products are defined
- **Associativity**: $(AB)C=A(BC)$ when the dimensions allow for these multiplications
- **Distributivity**: $A(B+C)=AB+AC$ and $(A+B)C=AC+BC$