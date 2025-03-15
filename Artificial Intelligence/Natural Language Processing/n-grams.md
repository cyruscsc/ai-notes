## Definition

- An *n*-gram is a sequence of *n* items from a sample of text

## Variants

- **Character *n*-gram**: the items are characters
- **Word *n*-gram**: the items are words
- **Unigram**: sequence of one item
- **Bigram**: sequence of two items
- **Trigram**: sequence of three items

## Characteristics

- Useful for text processing
- While the AI hasn’t necessarily seen the whole [[sentence]] before, it sure has seen parts of it
- Since some words occur together more often than others, it is possible to also predict the next word with some probability
	- E.g. a smartphone suggests words to you based on a [[probability distribution]] derived from the last few words you typed

## Example

> How often have I said to you that when you have eliminated the impossible whatever remains, however improbable, must be the truth?

- Bigrams: "how often", "often have", " have I"...
- Trigrams: "how often have", "often have I", "have I said"...
