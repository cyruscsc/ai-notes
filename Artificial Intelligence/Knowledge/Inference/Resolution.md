## Definition

- Combines two clauses that contain [[Unit Resolution#Complementary literals|complementary literals]]
- Produces a new clause that is logically implied by the original two

## Algorithm

- To determine if $KB\models\alpha$:
	- Convert $(KB\land\neg\alpha)$ to [[Conjunction Normal Form|CNF]] (for [[#Proof by contradiction|proof by contradiction]])
	- Keep checking to see if we can use [[Unit Resolution|resolution]] to produce a new clause
		- If ever we produce the [[#Empty clause|empty clause]], we have a contradiction, and $KB\models\alpha$
		- Otherwise, if we cannot add new clauses, no entailment

## Proof by contradiction

- To determine if $KB\models\alpha$:
	- Check: is $(KB\land\neg\alpha)$ a contradiction?
		- If so, then $KB\models\alpha$
		- Otherwise, no entailment

## Characteristics

- Use the [[Unit Resolution]] rule to draw inference
- Input clauses must be in [[Conjunction Normal Form|CNF]]
- Resolve [[Unit Resolution#Complementary literals|complementary clauses]] to get a new clause

### Refactoring

$$
\begin{gathered}
P\lor Q\lor S\\
\neg P\lor R\lor S\\
-------\\
(Q\lor S\lor R\lor S)\\
\Downarrow\\
(Q\lor R\lor S)
\end{gathered}
$$

- Remove duplicate literals
- E.g. $P\lor Q\lor S$ + $\neg P\lor R\lor S$ = $(Q\lor S\lor R\lor S)$ = $(Q\lor R\lor S)$

### Empty clause

$$
\begin{gathered}
P\\
\neg P\\
-----\\
()
\end{gathered}
$$

- Always false
- It is impossible that both $P$ and $\neg P$ are true

## Example

> Does $(A\lor B)\land(\neg B\lor C)\land(\neg C)$ entails $A$?

1. $(A\lor B)\land(\neg B\lor C)\land(\neg C)\land(\neg A)$
2. $(A\lor B)\quad\underline{(\neg B\lor C)}\quad\underline{(\neg C)}\quad(\neg A)\quad(\neg B)$
3. $\underline{(A\lor B)}\quad(\neg B\lor C)\quad(\neg C)\quad(\neg A)\quad\underline{(\neg B)}\quad(A)$
4. $(A\lor B)\quad(\neg B\lor C)\quad(\neg C)\quad\underline{(\neg A)}\quad(\neg B)\quad\underline{(A)}\quad()$
5. $(A\lor B)\land(\neg B\lor C)\land(\neg C)\models A$