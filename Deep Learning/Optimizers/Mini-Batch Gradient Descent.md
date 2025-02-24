## Approach

- Start with a random choice of weights
- Repeat:
	- Calculate the gradient based on **one small batch**: direction that will lead to decreasing loss
	- Update weights according to the gradient

## Characteristics

- Computes the gradient based on on a few points selected at random
- Finds a compromise between computation cost and accuracy