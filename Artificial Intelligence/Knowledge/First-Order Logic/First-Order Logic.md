## Symbols

### Constant symbol

- Represents an object
- E.g. Minerva, Pomona, Horace, Gilderoy, Gryffindor, Hufflepuff, Ravenclaw, Slytherin

### Predicate symbol

- A relation or function that takes an argument and return a boolean value
- E.g. Person, House, BelongsTo

### Examples

- $Person(Minerva)$: Minerva is a person
- $House(Gryffindor)$: Gryffindor is a house
- $\neg House(Minerva)$: Minerva is not a house
- $BelongsTo(Minerva, Gryffindor)$: Minerva belongs to Gryffindor

## Characteristics

- All the logical connectives work in first-order logic the same way as in [[Propositional Logic|propositional logic]]
- More succinct than propositional logic
	- First-order logic allows having one symbol for each person and one symbol for each house
	- Propositional logic requires each person-hose assignment to have a different symbol

## Quantification

$$
\forall x. Person(x)\rightarrow(\exists y. House(y)\land BelongsTo(x, y))
$$

- A combination of [[Universal Quantification]] and [[Existential Quantification]]
- For all objects `x`, if `x` is a person, then there exists an object `y` such that `y` is a house and `x` belongs to `y`
- Every person belongs to a house
