---
aliases:
  - ReLU
---

## Defintion

$$
g(z)=\text{max}(0,z)
$$
> $g(z)\ge0$
> if $z<0$, $g(z)=0$
> if $z\ge0$, $g(z)\ge0$

- Allows the output to be any positive value
- If the value is negative, ReLU sets it to 0
- Faster computation and learning than [[Sigmoid Function]]
- Goes flat in one place (left of graph)
