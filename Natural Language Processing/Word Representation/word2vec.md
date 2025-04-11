## Definition

- An algorithm for generating distributed representations of words
- Based on **skip-gram** architecture

## Skip-gram architecture

- A neural network architecture for predicting context given a target word
- 1 input layer
	- 1 unit for every target word
- 1 hidden layer
	- Usually 50 or 100 units, though this number is flexible
	- Every unit in this hidden layer is connected to every unit in the input layer
	- Generates values that represent the distributed representations of words
- 1 output layer
	- Generates words that are likely to appear in a similar context as the target words

## Applications

###  Generate words similar in meaning

#### Approach

- Find which other words in the corpus have the most similar vectors

#### Example

- `book` → `book`, `books`, `essay`, `memoir`, `essays`, `novella`, `anthology`, `blurb`, `autobiography`, `audiobook`

### Understand semantic similarities

#### Approach

- Compute the difference between words based on how different their vectors are

#### Examples

- `king`, `man`, `woman` → `queen`
	- The difference between `king` and `man` is similar to the difference between `queen` and `woman`
	- If we add the difference between `king` and `man` to the vector of `woman`, the closest word to the resulting vector is `queen`
- `ramen`, `japan`, `america` → `burritos`
	- The difference between `ramen` and `japan` is similar to the difference between `burritos` and `america`
	- If we add the difference between `ramen` and `japan` to the vector of `america`, the closest word to the resulting vector is `burritos`