## Definition

$$
a_{n+1}=f(a_n)
$$

> $f$: a function that defines the rule of evolution

- Models processes that evolve over time in discrete steps
- For linear system, $f(x)=bx$
	- Leading to $a_{n+1}=ba_n$, where $b$ is a constant
	- $b$ can be a [[Markov matrix]]

## Characteristics

- Has a sequence of states
- Each state depends on the previous state according to a specific rule or function

## Explicit solutions

$$
a_n=a_0b^n
$$

> $a_0$: initial state

- For linear systems, explicit formulas can be derived to compute the state at any time step without iterating through all previous steps

## Steady-state distribution

- The long-term behavior is governed by the [[Eigenvalue and Eigenvector|eigenvalues]] of the [[Markov matrix]]
- If the Markov matrix is irreducible (all states communicate) and aperiodic (no cyclic behavior), the system will converge to a unique steady-state vector regardless of the initial state
