## Definition

- A family of problems that optimize a linear equation

## Components

### Cost function

- A cost function that we want to minimize
- E.g. $c_1x_1+c_2x_2+\dots+c_nx_n$, where $c$ is the cost associated with variable $x$

### Constraint

- How much resources we can dedicate to this problem $b$
- A constraint that’s represented as a sum of variables that is
	- either less than or equal to a value $a_1x_1+a_2x_2+\dots+a_nx_n\le b$
	- or precisely equal to this value $a_1x_1+a_2x_2+\dots+a_nx_n=b$
	- where $a$ is the resource associated with variable $x$

### Individual bounds

- Individual bounds on variables of the form $l_i\le x_i\le u_i$
- E.g. a variable can’t be negative

## Algorithms

- Simplex
- Interior-Point

## Examples

> Machine $X_1$
> - Running cost: $50/hour
> - Required labor: 5 units/hour
> - Output: 10 units/hour

> Machine $X_2$
> - Running cost: $80/hour
> - Required labor: 2 units/hour
> - Output: 12 units/hour

> Company
> - Available labor: 20 units
> - Required output: 90 units

- Cost function: $50x_1+80x_2$
- Labor constraint: $5x_1+2x_2\le20$
- Output constraint: $10x_1+12x_2\ge90=-10x_1-12x_2\le-90$

## Code examples

```python
import scipy.optimize

# Objective Function: 50x_1 + 80x_2
# Constraint 1: 5x_1 + 2x_2 <= 20
# Constraint 2: -10x_1 + -12x_2 <= -90

result = scipy.optimize.linprog(
  [50, 80],  # Cost function: 50x_1 + 80x_2
  A_ub=[[5, 2], [-10, -12]],  # Coefficients for inequalities
  b_ub=[20, -90],  # Constraints for inequalities: 20 and -90
)

if result.success:
  print(f"X1: {round(result.x[0], 2)} hours")
  print(f"X2: {round(result.x[1], 2)} hours")
else:
  print("No solution")
```