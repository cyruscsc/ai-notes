---
aliases:
  - MLE
---

## Algorithm

1. Choose $n$ features $x_i$ that you think might be indicative of anomalous examples
2. Fit parameters $\mu_1,\ldots,\mu_n,\sigma^2_1,\ldots,\sigma^2_n$
$$
\begin{gathered}
\mu_j=\frac{1}{m}\sum_{i=1}^mx^{(i)}_j
\qquad
\sigma^2_j=\frac{1}{m}\sum_{i=1}^m(x^{(i)}_j-\mu_j)^2\\
\vec{\mu}=\frac{1}{m}\sum_{i=1}^m\vec{x}^{(i)}=
\begin{bmatrix}
\mu_1\\\vdots\\\mu_n
\end{bmatrix}
\end{gathered}
$$
3. Given new example $x$, compute [[Maximum Likelihood Estimation|MLE]]

## Equation

$$
\begin{gathered}
\begin{aligned}
p(x;\mu,\sigma^2)&=\frac{1}{\sqrt{2\pi}\sigma}e^{\frac{-(x-\mu)^2}{2\sigma^2}}\\
p(\vec{x})&=\prod_{j=1}^np(x_j;\mu_j,\sigma^2_j)\\
&=\prod_{j=1}^n\frac{1}{\sqrt{2\pi}\sigma_j}exp{(-\frac{(x_j-\mu_j)^2}{2\sigma_j^2}})\\
\end{aligned}\\
x=
\begin{cases}
\text{normal},&\text{if }p(x)\ge\epsilon\\
\text{anomaly},&\text{if }p(x)<\epsilon
\end{cases}
\end{gathered}
$$
> $p(x)$: probability of $x$ being in a dataset $\{x^{(1)},\ldots,x^{(m)}\}$
> $\sigma$: [standard deviation](#Standard%20deviation)
> $\mu$: [mean](#Mean)
> $\epsilon$: threshold of anomalies
