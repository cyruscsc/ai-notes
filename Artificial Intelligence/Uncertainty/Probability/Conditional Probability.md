## Definition

$$
P(a|b)=\frac{P(a\land b)}{P(b)}
$$

> $P(a|b)$: The probability of $a$ given $b$
> $P(a\land b)=P(b)P(a|b)=P(a)P(b|a)$

- The degree of belief in a proposition given some evidence that has already been revealed
- The probability that $a$ given $b$ is true = the probability of $a$ and $b$ being true $\div$ the probability of $b$
- We are interested in the events where both $a$ and $b$ are true (the numerator), but only from the worlds where we know $b$ to be true (the denominator)
- Dividing by $b$ restricts the possible worlds to the ones where $b$ is true

## Example

$$
\begin{aligned}
P(sum 12|6)&=\frac{P(sum 12\land6)}{P(6)}\\
&=\frac{\frac{1}{36}}{\frac{1}{6}}\\
&=\frac{1}{6}
\end{aligned}
$$
> $P(sum 12|6)$: the probability of rolling two dice and getting a sum of twelve, given that we have already rolled one die and got a six

1. Restrict our worlds to the ones where the value of the first die is six $P(6)$
2. Ask how many times does the event $a$ (the sum being 12) occur in the worlds that we restricted the question to (dividing by $P(b)$, or the probability of the first die yielding 6)
