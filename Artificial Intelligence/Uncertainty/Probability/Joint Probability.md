## Definition

$$
P(A\land B)=P(A)P(B)
$$

- The likelihood of multiple events all occurring
- Can be used to deduce [[Conditional Probability]]

## Example

| |R=rain|R=¬rain|
|:-:|:-:|:-:|
|C=cloud|0.08|0.32|
|C=¬cloud|0.02|0.58|

- The probabilities of clouds in the morning and rain in the afternoon
- Represents the co-occurrence of the events by joint probabilities
- To find the [[Probability Distribution]] of clouds in the morning given rain in the afternoon:

$$
\begin{aligned}
P(C|rain)&=\frac{P(C,rain)}{P(rain)}\\
&=\alpha P(C,rain)\\
&=\alpha<0.08,0.02>\\
&=<0.8,0.2>
\end{aligned}
$$

> $P(C,rain)$: interchangable with $P(C\land rain)$

1. Can view $P(rain)$ as some constant by which $P(C,rain)$ is multiplied
2. Factoring out $\alpha$ leaves us with the proportions of the probabilities of the possible values of $C$ given $rain$
	- If there is rain in the afternoon, the proportion of the probabilities of clouds in the morning and no clouds in the morning is 0.08:0.02
3. Normalize the values by computing $\alpha$
	- Such that $\alpha 0.08+\alpha 0.02=1$
4. Finally, $P(C|rain)=<0.8,0.2>$
