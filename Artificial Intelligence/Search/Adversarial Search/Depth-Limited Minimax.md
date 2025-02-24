## Characteristics

- Considers only a pre-defined number of moves before it stops
	- Without ever getting to a terminal state
- Does not allow for getting a precise value for each action
	- Since the end of the hypothetical games has not been reached
- Relies on an *evaluation function*
	- Estimates the expected utility of the game from a given state
	- Or, in other words, assigns values to states
	- The better the evaluation function, the better the Minimax algorithm that relies on it
	- Quality of the evaluation function $\propto$ performance of the Minimax algorithm
