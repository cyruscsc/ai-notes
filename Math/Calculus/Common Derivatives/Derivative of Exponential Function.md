## Definition

$$
f'(x)=e^x
$$

> For $f(x)=e^x$, where the Euler's number $e=\lim_{n\to\infty}(1+\frac{1}{n})^n$

## Proof

$$
\begin{aligned}
f'(x)&=\lim_{h\to0}\frac{e^{x+h}-e^x}{h}\\
&=\lim_{h\to0}\frac{e^xe^{h}-e^x}{h}\\
&=\lim_{h\to0}\frac{e^x(e^h-1)}{h}\\
&=e^x\lim_{h\to0}\frac{e^h-1}{h}\\
&=e^x\times1\\
&=e^x
\end{aligned}
$$

> $\lim_{h\to0}\frac{e^h-1}{h}=1$
