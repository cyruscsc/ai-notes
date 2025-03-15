## Definition

- The task of splitting a sequence of characters into pieces (tokens)
- Required to be able to look at [[n-grams]], since those rely on sequences of tokens

## Tokens

- **Word tokenization**: words as tokens
- **Sentence tokenization**: sentences as tokens

## Possible challenges

- Splitting the text into words based on the space character may end up with words with punctuation
	- E.g. "remains,"
- Cannot simply remove punctuation from words with apostrophes and hyphens
	- E.g. "o'clock", "pearl-grey"
- Some punctuation is important for [[sentence]] structure
	- E.g. periods
- Some punctuation may appear at the end of a word or a sentence
	- E.g. "Mr.", "goodbye."
