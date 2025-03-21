> An inverse function $f^{-1}$ reverses the operation of a given function $f$

## Definition

$$
(f^{-1})’(x)=\frac{1}{f’(f^{-1}(x))}
$$

> $f(x)$: the function
> $f^{-1}(x)$: the inverse function of $f$
> $f'(x)$: the derivative of $f$
> $(f^{-1})’(x)$: the derivative of $f^{-1}(x)$

## Intuition

- Given $f(x)$ and $g(y)=f^{-1}(f(x))$
- Then, $f'(x)=\frac{\Delta f}{\Delta x}$ and $g'(y)=\frac{\Delta g}{\Delta y}=\frac{\Delta x}{\Delta f}$, since $y=f(x)$ and $x=g(y)$
- Therefore, $g'(y)=\frac{1}{f'(x)}$

## Example

Given $f^{-1}(x)=\sqrt{x}$ and $f(f^{-1}(x))=(f^{-1}(x))^2$

Let $x=4$, we have $f^{-1}(4)=2$ and $f(2)=4$

$f'(f^{-1}(x))=2(f^{-1}(x))=4$ (see [[Derivatives of Power Functions]])

$(f^{-1})’(x)=\frac{1}{4}$
