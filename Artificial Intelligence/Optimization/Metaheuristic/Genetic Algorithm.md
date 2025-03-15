---
aliases:
  - GA
---


## Definition

- A class of optimization and search algorithms inspired by the principles of biological evolution, particularly natural selection, genetic variation, and survival of the fittest
- A subset of evolutionary algorithms

## Characteristic

- Can simulate many points in any given parameter space
- Has a higher likelihood of finding optimal global solution

## Components

### Population

- A set of candidate solutions (individuals) represented as chromosomes
- Often in the form of binary strings or other encodings

### Fitness function

- Evaluates how well each individual solves the problem
- Higher fitness indicates better solutions

### Selection

- Chooses the fittest individuals to reproduce
- Ensures the survival of advantageous traits
- E.g. tournament selection, roulette wheel selection

### Crossover

- Combines parts of two parent solutions to produce offspring
- Introduces variability by mixing their characteristics to inherit desirable traits
- E.g. single-point crossover, two-point crossover, uniform crossover

### Mutation

- Randomly alters parts of a solution to maintain diversity
- To explore new areas of solution space to avoid local optima

## Workflow

- Initialize a random [[#Population|population]]
- Evaluate [[#Fitness function|fitness]] for each individual
- [[#Selection|Select]] parents based on fitness
- Apply [[#Crossover|crossover]] and [[#Mutation|mutation]] to generate a new population
- Repeat until a termination condition is met
	- E.g. max generation, satisfactory solution

## Advantages

- Effective for non-linear, multi-modal problems with large search spaces
- Does not require gradient information, unlike traditional optimization techniques

## Limitations

- Computationally expensive due to iterative evaluations
- May converge prematurely to suboptimal solutions if diversity is not maintained

## Applications

- [[Optimization]]
	- Engineering design problem
	- Scheduling
	- Resources allocation
- [[Machine Learning]]
	- [[Feature selection]]
	- Hyperparameter tuning
	- [[Neural networks]] optimization
- Finance
	- Portfolio optimization
	- Risk management
- Game development
	- AI behaviour modelling

## Parameters

### Parameter tuning

- Finds good values for parameters before algorithm runs
	- Experiment with different values
	- Select the ones that give best results
- Can be time-consuming

### Parameter control

- Allows for values of parameters to be changed while algorithm is running
- Allows for parameter values to be repeatedly optimized at different stages of the run

## Constraints

### Direct constraints handling

- Involves explicitly ensuring that individuals in population satisfy constraints during the algorithm's operations

#### Elimination

- Perform feasibility check before evaluating fitness of individuals
- Reject individuals that violate any constraints

#### Repair mechanism

- Apply repair method to offspring that violates constraints
- Can involve adjusting variable values or re-encoding solution

#### Boundary enforcement

- Ensure that individuals remain within specified bounds during crossover or mutation processes
- Directly enforce constraints at the point of genetic operations

### Indirect constraint handling

- Does not focus on enforcing constraints at every stage 
- Incorporates constraints into design of algorithm to naturally evolve feasible solutions

#### Penalty

- Attach penalty to fitness score of individual that violates constraints
- Infeasible solutions are less likely to be selected for reproduction

#### Decoding and encoding

- Encoding of solutions can be designed to inherently respect the constraints
- E.g. use specific representation that naturally limits search space to feasible solutions

#### Fitness landscape shaping

- Fitness function is designed a way that feasible solutions are favoured
- E.g. landscape modification, where the fitness of infeasible solutions is altered so they are less likely to survive

#### Selective pressure

- Selection mechanism can be biased towards selecting individuals that are more likely to be feasible
- Population evolves over time to favour individuals that naturally conform to the constraints

#### Multi-objective optimization

- Constraints can be treated as additional objectives
- Allows GA to explore trade-offs between objectives and constraints
- Leads to a set of Pareto-optimal solutions

## Pseudocode

```
input: n, x, u
gen = 0
init pop[gen]
pop[gen].add(generate_pop(num=n))
pop[gen].forEach: compute fitness
while pop[gen].fittest is not high enough:
  init pop[gen+1]
  members = select(from=pop[gen], num=(1-x)*n)
  pop[gen+1].add(members)
  offspring = crossover(from=pop[gen], num=x*n)
  pop[gen+1].add(offspring)
  pop[gen+1].mutate(num=u*n)
  pop[gen+1].forEach: compute fitness
  gen++
return pop[gen].fittest
```
