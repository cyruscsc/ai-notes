---
aliases:
  - Stochastic Matrix
  - Transition Matrix
---

## Definition

- A square matrix used to describe the transitions of a [[Markov chain]]

## Characteristics

- **Non-negative entries**: all entries in the matrix are non-negative 
	- They represent probabilities
	- Probabilities cannot be negative
- **Column sums equal to one**: each column of the matrix sums to one
	- Can be row instead, depending on the convention
	- Ensures that the total probability of transitioning from one state to all possible states is 100%

## Eigenvalues and eigenvectors

- The largest [[Eigenvalue and Eigenvector|eigenvalue]] $\lambda$ is always 1
- Its corresponding [[Eigenvalue and Eigenvector|eigenvector]] represents the steady-state distribution
- The steady-state distribution has to be normalized so that its entries sum to 1

## Types of Markov matrices

### Regular Markov matrix

- Some power of it has all positive entries
- Every state can be reached from any other state in a finite number of steps

### Singular Markov matrix

- Not regular Markov matrix
- Some states cannot be reached from others
