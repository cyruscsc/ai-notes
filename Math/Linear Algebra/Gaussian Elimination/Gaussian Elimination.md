## Definition

- A systematic method for solving systems of linear equations, finding the rank of a matrix, or determining the inverse of a matrix

## Related concepts

- [[Rank of a matrix]]
- [[Row echelon form]]
- [[Reduced row echelon form]]

## Row operations

- Transform a given matrix into its [[row echelon form]] (and optionally into [[reduced row echelon form]])

### Swapping rows

- Interchanging two rows

### Scaling rows

- Multiplying a row by a non-zero scalar

### Adding/subtracting rows

- Adding or subtracting a multiple of one row to another

## Approach

### Augmented matrix

- Represent the system of equations as an augmented matrix combining the coefficients and constants

### Forward elimination

- Begin with the first column and make all entries below the pivot zero by [[#row operations]]
- Move to subsequent columns, repeating the process until the matrix is in [[row echelon form]]

### Back substitution

- Cancel values above each pivot by [[#row operations]] to achieve [[reduced row echelon form]]
- Solve for variables starting from the last row

## Examples

### Non-singular system

Given a system:

$$
\begin{aligned}
2a-b+c&=1\\
2a+2b+4c&=-2\\
4a+b&=-1
\end{aligned}
$$

1. Represent as an augmented matrix

$$
\left[
\begin{array}{ccc|c}
2&-1&1&1\\
2&2&4&-2\\
4&1&0&-1
\end{array}
\right]
$$

2. Apply forward elimination to achieve row echelon form with pivots = 1

$$
\left[
\begin{array}{ccc|c}
1&-\frac{1}{2}&\frac{1}{2}&\frac{1}{2}\\
0&1&1&-1\\
0&0&1&0
\end{array}
\right]
$$

- For $C_1$
	- $R_1\leftarrow\frac{1}{2}R_1$
	- $R_2\leftarrow R_2-2R_1$
	- $R_3\leftarrow R_3-4R_1$
- For $C_2$
	- $R_2\leftarrow\frac{1}{3}R_2$
	- $R_3\leftarrow R_3-3R_2$
- For $C_3$
	- $R_3\leftarrow-\frac{1}{5}R_3$

3. Apply back substitution

$$
\left[
\begin{array}{ccc|c}
1&0&0&0\\
0&1&0&-1\\
0&0&1&0
\end{array}
\right]
$$

- For $C_3$
	- $R_1\leftarrow R_1-\frac{1}{2}R_3$
	- $R_2\leftarrow R_2-R_3$
- For $C_2$
	- $R_1\leftarrow R_1+\frac{1}{2}R_2$

Result:

$$
\begin{aligned}
a&=0\\
b&=-1\\
c&=0
\end{aligned}
$$

### Singular system with infinite solutions

Given a system:

$$
\begin{aligned}
a+2b-c&=5\\
2a+4b+5c&=1\\
3a+6b+4c&=6
\end{aligned}
$$

After row deduction:

$$
\left[
\begin{array}{ccc|c}
1&2&-1&5\\
0&0&-7&9\\
0&0&0&0
\end{array}
\right]
$$

- The system has infinite solutions
- $R_3$ implies $0a+0b+0c=0$

### Singular system with no solutions

Given a system:

$$
\begin{aligned}
a+2b-c&=5\\
2a+4b+5c&=1\\
3a+6b+4c&=10
\end{aligned}
$$

After row deduction:

$$
\left[
\begin{array}{ccc|c}
1&2&-1&5\\
0&0&-7&9\\
0&0&0&4
\end{array}
\right]
$$

- The system has no solutions
- $R_3$ implies $0a+0b+0c=4$
