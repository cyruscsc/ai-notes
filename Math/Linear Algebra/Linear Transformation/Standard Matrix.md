## Standard matrix

## Definition

$$
A=
\left[
\begin{array}{c|c|c}
v_1&\dots&v_n
\end{array}
\right]\quad\text{for }v_i=T(e_i)
$$

> $e_i$: $i^{th}$ basis vector in the vector space

- A matrix that describes the effect of a [[linear transformation]] on the standard basis vectors of a vector space

## Example

Given the basis vectors $e_1=\begin{bmatrix}1\\0\end{bmatrix}$ and $e_2=\begin{bmatrix}0\\1\end{bmatrix}$, and the corresponding images $v_1=\begin{bmatrix}3\\-1\end{bmatrix}$ and $v_2=\begin{bmatrix}2\\3\end{bmatrix}$

$$
\begin{gathered}
\text{Given}
\begin{cases}
T(e_1)=Ae_1=v_1\\
T(e_2)=Ae_1=v_2
\end{cases}\\\\
A=
\left[
\begin{array}{c|c}
v_1&v_2
\end{array}
\right]=
\begin{bmatrix}
3&2\\
-1&3
\end{bmatrix}
\end{gathered}
$$