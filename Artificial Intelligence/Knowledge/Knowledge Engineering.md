## Definition

- The process of figuring out how to represent propositions and logic in AI

## Examples

### Clue

#### Game rules

- A murder was committed by a person, using a tool in a location
- People, tools, and locations are represented by cards
- One card of each category is picked at random and put in an envelope
- Participants uncover whodunnit by uncovering cards and deducing from these clues what must be in the envelope
- Game starts with each player seeing one person, one tool, and one location
- Players do not share the information that they saw in these cards

#### Setting

- People:
	- Mustard
	- Plum
	- Scarlet
- Tools:
	- Knife
	- Revolver
	- Wrench
- Locations:
	- Ballroom
	- Kitchen
	- Library

#### Approach

1. Start creating our knowledge base by adding the rules of the game
	- (Mustard ∨ Plum ∨ Scarlet)
	- (knife ∨ revolver ∨ wrench)
	- (ballroom ∨ kitchen ∨ library)
2. Add cards that our player gets
	- ¬(Mustard)
	- ¬(kitchen)
	- ¬(revolver)
3. Add combination of a wrong guess
	- (¬Scarlet ∨ ¬library ∨ ¬wrench)
4. Add the card that another player shows us
	- ¬(Plum)
5. At this point, we can conclude that the murderer is Scarlet
6. Add another card that another player shows us
	- ¬(ballroom)
7. Now we can deduce that Scarlet committed the murder with a knife in the library

#### Code samples

```python
knowledge = And(

  # Start with the game conditions:
  # one item in each of the three categories has to be true
  Or(mustard, plum, scarlet),
  Or(ballroom, kitchen, library),
  Or(knife, revolver, wrench),

  # Add the information from the three initial cards we saw
  Not(mustard),
  Not(kitchen),
  Not(revolver),

  # Add the guess someone made that it is Scarlet, 
  # who used a wrench in the library
  Or(Not(scarlet), Not(library), Not(wrench)),

  # Add the cards that we were exposed to
  Not(plum),
  Not(ballroom)
)
```

### Houses

#### Setting

- There is exactly one person in each house
- People:
	- Gilderoy
	- Pomona
	- Minerva
	- Horace
- Houses:
	- Gryffindor
	- Hufflepuff
	- Ravenclaw
	- Slytherin

#### Approach

1. Each of the possible assignments will have to be a proposition in itself
	- MinervaGryffindor
	- MinervaHufflepuff
	- MinervaRavenclaw
	- MinervaSlytherin
	- PomonaGryffindor
	- and so on for every assignment
2. Represent that each person belongs to a house
	- An Or statement is required with all the possible house assignments per person
	- (MinervaGryffindor ∨ MinervaHufflepuff ∨ MinervaRavenclaw ∨ MinervaSlytherin)
	- and so on for every person
3. Encode that if one person is assigned to one house, they are not assigned to the other houses
	- (MinervaGryffindor → ¬MinervaHufflepuff) ∧ (MinervaGryffindor → ¬MinervaRavenclaw) ∧ (MinervaGryffindor → ¬MinervaSlytherin) ∧ (MinervaHufflepuff → ¬MinervaGryffindor)
	- and so on for all houses and all people

#### Limitation

- Representing the puzzle’s conditions in [[propositional logic]] is quite cumbersome
- A solution to this inefficiency is offered in the section on first order logic
