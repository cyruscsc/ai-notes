## Topics

- [[Conjunction Normal Form]]
- [[Propositional Theorem Proving]]

## Propositional symbols

- Most often letters (P, Q, R) that are used to represent a proposition

## Logic connectives

- Logical symbols that connect propositional symbols in order to reason in a more complex way about the world
- [[Not ¬]]
- [[And ∧]]
- [[Or ∨]]
- [[Implication →]]
- [[Biconditional ↔]]
- [[Entailment ⊨]]

## Concepts

### Clause

- A disjunction of literals
- E.g. $P\lor Q\lor R$

### Literal

- A propositional symbol or the opposite of a propositional symbol
- E.g. $P$, $\neg Q$

### Conjunction

- Things connected with And

### Disjunction

- Things connected with Or

### Model

- An assignment of truth values to all propositional variables in a given set
- A precise representation of a possible world
- Assignment of a truth value to every propositional symbol (a "possible world")
- Propositions are statements about the world that can be either true or false
	- Knowledge about the world is represented in the truth values of these propositions
	- The model is the truth-value assignment that provides information about the world

### Knowledge base

- A set of propositions assumed to be true
- A set of sentences known by a [[Knowledge#Knowledge-based agents|knowledge-based agent]]
- This is knowledge that the AI is provided about the world in the form of propositional logic sentences that can be used to make additional inferences about the world

### Grounding

- Captures the connection between logical reasoning processes and the real environment in which the agent exists
- The agents sensors create a connection between the world and the knowledge base
- The meaning and truth of percept sentences are defined by the processes of sensing and sentence construction that produce them
- Learning is fallible as our observation of a particular fact may not generalize
