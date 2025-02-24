---
aliases:
  - CNF
---

## Definition

- Logical sentence that is a conjunction of clauses
- E.g. $(A\lor B\lor C)\land(D\lor\neg E)\land(F\lor G)$

## Conversion to CNF

### Approach

- Eliminate biconditionals
	- Use [[Biconditional Elimination]]
	- E.g. turn $(\alpha\leftrightarrow\beta)$ into $(\alpha\rightarrow\beta)\land(\beta\rightarrow\alpha)$
- Eliminate implications
	- Use [[Implication Elimination]]
	- E.g. turn $(\alpha\rightarrow\beta)$ into $\neg\alpha\lor\beta$
- Move $\neg$ inwards
	- Use [[De Morgan's Law]]
	- E.g. turn $\neg(\alpha\land\beta)$ into $\neg\alpha\lor\neg\beta$
- Distribute $\land$ wherever possible
	- Use [[Distributive Property]]

### Example

$$
\begin{gathered}
(P\lor Q)\rightarrow R\\
\Downarrow\\
\neg(P\lor Q)\lor R\\
\Downarrow\\
(\neg P\land\neg Q)\lor R\\
\Downarrow\\
(\neg P\lor R)\land(\neg Q\lor R)
\end{gathered}
$$

