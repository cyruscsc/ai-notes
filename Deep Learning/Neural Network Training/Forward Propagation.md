---
aliases:
  - Forward Prop
---

## Definition

$$
\begin{aligned}
\text{for }l=1\text{ to }n\text{,}
\qquad\vec{a}^{[l]}=
\begin{bmatrix}
g(\vec{w}^{[l]}_1\cdot\vec{a}^{[l-1]}+b^{[l]}_1)\\
\vdots\\
g(\vec{w}^{[l]}_j\cdot\vec{a}^{[l-1]}+b^{[l]}_j)\\
\end{bmatrix}
\end{aligned}
$$
> $\vec{a}^{[l]}$: vector of activation values (output) of layer $l$
> $\vec{a}^{[l-1]}$: vector of activation values (output) from previous layer
> $\vec{w}^{[l]}_j,b^{[l]}_j$: parameters of layer $l$, unit (neuron) $j$
> $n$: number of layers

- Make computation in forward direction from left to right (layer 1 to layer n)
