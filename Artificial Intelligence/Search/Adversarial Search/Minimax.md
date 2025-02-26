## Characteristics

- `MIN` aims to minimize score
- `MAX` aims to maximize score
- Represents winning conditions as (-1) for one side and (+1) for the other side
- Can be optimized by [[Alpha-Beta Pruning]] or [[Depth-Limited Minimax]]

## Components

- `s0`: initial state
- `Player(s)`
	- Input: state `s`
	- Output: which player's turn it is
- `Actions(s)`
	- Input: state `s`
	- Ouput: all legal moves in this state
- `Result(s, a)`
	- Input: state `s`, action `a`
	- Output: new state
- `Terminal(s)`
	- Input: state `s`
	- Output: whether this is the last step in the game (`True` or `False`)
- `Utility(s)`
	- Input: state `s`
	- Output: utility value of state (`-1`, `0`, or `1`)

## Algorithm

- Recursively simulates all possible games that can take place
	- Beginning at the current state
	- Until a terminal state is reached 
- Each terminal state is valued as either (-1), 0, or (+1)
- Creates values for the state that would result from each possible action
	- Alternating between `MAX` and `MIN`

## Pseudocode

- Given a state `s`
	- The `MAX` player picks action `a` in Actions(s) that produces the highest value of `Min-Value(Result(s, a))`
	- The `MIN` player picks action `a` in Actions(s) that produces the lowest value of `Max-Value(Result(s, a))`

### Max-Value function

```
MAX-VALUE(state):
  v = -inf
  if Terminal(state):
    return Utility(state)
  for action in Actions(state):
    v = MAX(v, MIN-VALUE(Result(state, action)))
  return v
```

### Min-Value function

```
MIN-VALUE(state):
  v = inf
  if Terminal(state):
    return Utility(state)
  for action in Actions(state):
    v = MIN(v, MAX-VALUE(Result(state, action)))
  return v
```
