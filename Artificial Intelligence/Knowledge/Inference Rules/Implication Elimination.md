## Definition

$$
\begin{gathered}
\alpha\rightarrow\beta\\
-----\\
\neg\alpha\lor\beta
\end{gathered}
$$

- An implication is equivalent to an Or relation between the negated antecedent and the consequent
- E.g. "If it is raining, Harry is inside" = "(it is not raining) or (Harry is inside)"

## Truth table

|P|Q|P → Q|¬P ∨ Q|
|:-:|:-:|:-:|:-:|
|false|false|true|true|
|false|true|true|true|
|true|false|false|false|
|true|true|true|true|

- $P\rightarrow Q$ and $\neg P\lor Q$ are equivalent logically
	- They have the same truth-value assignment
- An implication is true if either of two possible conditions is met:
	1. If the antecedent is false, the [[Propositional Logic#Implication →|implication]] is trivially true
		- Represented by the negated antecedent $P$ in $\neg P\lor Q$
		- The proposition is always true if $P$ is false
	2. If the antecedent and the consequent are both true
		- If $P$ and $Q$ are both true, then $\neg P\lor Q$ is true
		- If $P$ is true and $Q$ is not, then $\neg P\lor Q$ is false
