## Concepts

- [[Markov Assumption]]
- [[Markov Chain]]
- [[Hidden Markov Model]]
- [[Sensor Markov Assumption]]

## Characteristics

- Represents the variable of time by $X_t$
- Allows predicting events in the future

## Text generation

- Can be used to generate text in [[Natural Language Processing|NLP]]
- Train the model on a text
- Establish probabilities for every *n*-th token in an [[n-grams|n-gram]] based on the *n* words preceding it
- E.g. using trigrams, after the model has two words:
	- It can choose a third word from a probability distribution based on the first two words
	- It can choose a fourth word from a probability distribution based on the second and third words
