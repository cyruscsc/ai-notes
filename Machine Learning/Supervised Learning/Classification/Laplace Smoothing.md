---
aliases:
  - Add-One Smoothing
---

## Definition

$$
P(w|c)=\frac{count(w,c)+\alpha}{count(c)+\alpha K}
$$

> $count(w,c)$: number of times word $w$ appears in class $c$
> $count(c)$: total word count in class $c$
> $K$: total number of unique features
> $\alpha>0$: smoothing parameter

- Adds a small constant (commonly 1) to both the numerator and denominator of the probability calculation
- Addresses the problem of zero probabilities
