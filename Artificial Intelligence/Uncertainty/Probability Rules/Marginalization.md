## Definition

### General

$$
P(a)=P(a,b)+P(a,\neg b)
$$

- $b$ and $\neg b$ are disjoint probabilities
	- The probability of $b$ and $\neg b$ occurring at the same time is 0
	- $b$ and $\neg b$ [[Probability#Axioms in probability|sum up to 1]]
- When $a$ happens, $b$ can either happen or not
- The probability of both $a$ and $b$ happening + the probability of $a$ and $\neg b$ = the probability of $a$

### Random variables

$$
P(X=x_i)=\sum_jP(X=x_i,Y=y_j)
$$

- Left part: the probability of [[Random Variable]] $X$ having the value $x_i$
- Right part: sum of all the [[Joint Probability|joint probabilities]] of $x_i$ and every single value of the [[Random Variable]] $Y$
- E.g. $P(C=cloud)=P(C=cloud,R=rain)+P(C=cloud,R=\neg rain)$$=0.08+0.32=0.4$