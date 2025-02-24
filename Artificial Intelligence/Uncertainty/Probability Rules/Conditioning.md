## Definition

### General

$$
P(a)=P(a|b)P(b)+P(a|\neg b)P(\neg b)
$$

- The probability of event $a$ occurring = the probability of $a$ given $b$ $\times$ the probability of $b$ + the probability of $a$ given $\neg b$ $\times$ the probability of $\neg b$

### Random variables

$$
P(X=x_i)=\sum_jP(X=x_i|Y=y_j)P(Y=y_j)
$$

- The [[Random Variable]] $X$ takes the value $x_i$ with probability that is equal to the sum of the probabilities of $x_i$ given each value of the [[Random Variable]] $Y$ multiplied by the probability of variable $Y$ taking that value
- Multiply $P(a|b)={P(a,b)}{P(b)}$ by $P(b)$, end up with $P(a,b)$  (see [[Conditional Probability]])
- Then do the same as we did with [[Marginalization]]