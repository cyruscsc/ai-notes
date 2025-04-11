## Definition

- The text is abstracted from its meaning to represent the structure of the [[Sentence]] using formal grammar
- Where **formal grammar** is a system of rules for generating sentences in a language

## Characteristics

- Using formal grammar, the AI is able to represent the structure of sentences
- To represent more complex sentences, we will have to add more rules to our formal grammar

## Syntax tree

> "She saw the city"

```
     S
 ┌───┴──┐
 NP     VP
 │   ┌──┴──┐
 │   V     NP
 │   │   ┌─┴─┐
 N   │   D   N
 │   │   │   │
she saw the city
```

- Assign each word its part of speech
	- `N`: noun
	- `V`: verb
	- `D`: determiner
- Represent how words in are connected to each other
	- `NP`: noun phrase
	- `VP`: verb phrase

## Code example

```python
import nltk

grammar = nltk.CFG.fromstring("""
  S -> NP VP

  NP -> D N | N
  VP -> V | V NP

  D -> "the" | "a"
  N -> "she" | "city" | "car"
  V -> "saw" | "walked"
""")

parser = nltk.ChartParser(grammar)

sentence = input("Sentence: ").split()
try:
  for tree in parser.parse(sentence):
    tree.pretty_print()
    tree.draw()
except ValueError:
  print("No parse tree possible.")
```
