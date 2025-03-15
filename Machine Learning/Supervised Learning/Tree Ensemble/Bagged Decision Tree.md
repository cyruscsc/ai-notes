## Definition

- Given a training set of size $m$, for $b=1$ to $B$:
	- Use [[#sampling with replacement]] to create a new training set of size $m$
	- Train a [[decision tree]] on the new training set

> Note: choice of $B$ can be around 100 (64, 128, etc.)

## Sampling with replacement

- Construct new training set that is a bit similar to, but also pretty different from the original training set
1. Put all examples into a theoretical bag
2. Randomly pick one example and add to new training set
3. Put the example back into the bag
4. Repeat random picking until the new training set if of the same size as the original training set
