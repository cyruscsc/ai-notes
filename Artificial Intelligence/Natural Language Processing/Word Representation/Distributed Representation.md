## Definition

- The meaning of each word is distributed across multiple values in a vector

## Algorithms

- [[word2vec]]

## Characteristics

- Each vector has a limited number of values
- Allows us to generate unique values for each word while using smaller vectors
- Able to represent similarity between words by how different the values in their vectors are
- Can define words by their adjacent words
	- Follows the idea of "you shall know a word by the company it keeps"
	- By considering the environment in which a certain word tends to appear, we can infer the meaning of the word

## Example

> "He wrote a book"

- `[-0.34,-0.08,0.02,-0.18,...]`: he
- `[-0.27,0.40,0.00,-0.65,...]`: wrote
- `[-0.12,-0.25,0.29,-0.09,...]`: a
- `[-0.23,-0.16,-0.05,-0.57,...]`: book