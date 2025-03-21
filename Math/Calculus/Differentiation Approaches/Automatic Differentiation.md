## Definition

- A set of techniques for efficiently and accurately computing [[Derivative|derivatives]] of functions implemented as computer programs

## Characteristics

- Combines aspects of both [[Symbolic Differentiation|symbolic]] and [[Numerical Differentiation|numerical]] methods
- Exploits the fact that every computation is a sequence of elementary operations
- Applies the chain rule repeatedly to these operations
- Computes derivatives to machine precision without the need for symbolic expressions
- Important in [[machine learning]], especially for implementing [[backpropagation]] in [[neural networks]]

## Modes

### Forward mode

- Propagates derivatives from inputs to outputs

### Reverse mode

- Propagates derivatives from outputs to inputs
- Especially efficient for functions with many inputs and few outputs
