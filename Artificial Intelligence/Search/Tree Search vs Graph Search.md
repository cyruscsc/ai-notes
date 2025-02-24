## Overview

- Both work on tree and graph data structure
- Both implement a [[Search Problems#Frontier|frontier]]
- Graph search use a data structure called explored set

## Tree search

- Starts with a frontier that contains the initial state of the problem
- Repeat:
	- If frontier is empty, return no solution
	- Pop a node from frontier for expansion
	- If the node contains goal state, return solution
	- Otherwise, expand the node and add resulting nodes to the frontier

## Graph search

- Starts with a frontier that contains the initial state of the problem
- Starts with an empty explored set
- Repeat:
	- If frontier is empty, return no solution
	- Pop a node from frontier for expansion
	- If the node contains goal state, return solution
	- Add the node to the explored set
	- Otherwise, expand the node and add resulting nodes to the frontier if the nodes are not already in the frontier or the explored set