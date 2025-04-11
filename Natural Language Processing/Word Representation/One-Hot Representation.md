## Definition

- Each word is represented with a vector that consists of as many values as we have words

## Characteristics

- Except for a single value in the vector that is equal to `1`, all other values are equal to `0`
- Words are differentiated by the values of `1`, ending up with a unique vector per word

## Limitations

- The vector length depends on the total number of words represented
	- E.g. if there are 50000 words, then there will be 50000 vectors of length 50000
- Words with similar meanings have entirely different representation

## Example

> "He wrote a book"

- `[1,0,0,0]`: he
- `[0,1,0,0]`: wrote
- `[0,0,1,0]`: a
- `[0,0,0,1]`: book