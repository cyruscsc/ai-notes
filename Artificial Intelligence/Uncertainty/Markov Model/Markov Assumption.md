## Definition

- The assumption that the current state depends on only a finite fixed number of previous states

## Example

> Predicting weather

- It is infeasible to use all the data from the past year to predict tomorrow’s weather
	- The computational power required is high
	- There is probably no information about the [[Conditional Probability]] of tomorrow’s weather based on the weather 365 days ago
- Using the Markov assumption, we restrict our previous states, thereby making the task manageable
	- E.g. how many previous days we are going to consider when predicting tomorrow’s weather
- We might get a more rough approximation of the probabilities of interest, but this is often good enough for our needs
