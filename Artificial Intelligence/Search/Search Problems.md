## Components

### Agent

- An entity that perceives its environment and acts upon that environment

### State

- A configuration of an agent in its environment

#### Initial state

- The state from which the search algorithm starts

#### State space

- The set of all states reachable from the initial state by any sequence of actions
- Can be visualized as a directed graph
	- Nodes = states
	- Edges = actions

#### Repeated state

- Can give rise to loopy paths, which in turn make the complete search tree infinite

#### Loopy path

- A special case of redundant paths
- Exists whenever there is more than one way of getting from one state to another

### Actions

- Choices that can be made in a state
- Not all actions are available in all circumstances
- `Actions(s)`
	- Input: state `s`
	- Output:  set of actions that can be executed in state `s`

#### Transition model

- A description of what state results from performing any applicable action in any state
- Maps a state and an action to a resulting state
- `Result(s, a)`
	- Input: state `s`, action `a`
	- Output: state resulting from performing action `a` in state `s`

#### Path cost

- A numerical cost associated with a given path

#### Cost function

- A function that applies a cost to each action

### Solution

- A sequence of actions that leads from the initial state to the goal state

#### Optimal solution

- A solution that has the lowest path cost among all solutions

#### Goal test

- The condition that determines whether a given state is a goal state

## Infrastructure

### Node

- A data structure that contains:
	- `state`
	- `parent`
	- `action` that was applied to `parent` to get to the current `state`
	- `path cost` from the initial state to this node

### Frontier

- The mechanism that "manages" the *nodes*
- Set of all nodes available for expansion at given point
- Starts by containing an initial state and an empty set of explored items
- Repeats:
	1. If the frontier is empty, return no solution
	2. Remove a node from the frontier
	3. If the node contains the goal state, return the solution
	Else, expand the node and add resulting nodes to the frontier, then add the current node to the explored set
- Can be implemented as a queue, a stack, or a priority queue