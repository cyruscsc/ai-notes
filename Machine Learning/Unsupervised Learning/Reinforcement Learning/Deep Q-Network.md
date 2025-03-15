---
aliases:
  - DQN
---

## Definition

- Train a neural network that inputs current state and action to compute $Q(s,a)$

## Continuous state space

- Possible states that an agent can be in are described by continuous set of values

## Intuition

1. In state $s$, use neural network to compute
	- $Q(s,nothing)$
	- $Q(s,left)$
	- $Q(s,main)$
	- $Q(s,right)$
2. Pick action $a$ that maximizes $Q(s,a)$

## Architecture

- Input layer $\vec{x}=\begin{bmatrix}s\\a\end{bmatrix}$: 12 units 
- Hidden layer 1: 64 units
- Hidden layer 2: 64 units
- Output layer $y=Q(s,a)$: 1 unit

$$
\begin{aligned}
s=
\begin{bmatrix}
x\\y\\\dot{x}\\\dot{y}\\\theta\\\dot{\theta}\\l\\r
\end{bmatrix}
&&a=
\begin{bmatrix}
nothing\\left\\main\\right
\end{bmatrix}
\end{aligned}
$$
> $s$: state
> $a$: action
> $x$: horizontal position
> $y$: vertical position
> $\dot{x}$: horizontal velocity
> $\dot{y}$: vertical velocity
> $\theta$: tilt angle
> $\dot{\theta}$: angular velocity
> $l$: left leg grounded
> $r$: right leg grounded
> $nothing$: do nothing
> $left$: fire left thruster
> $main$: fire main thruster
> $right$: fire right thruster

## Learning algorithm

$$
f_{w,b}(x)\approx{y}
$$
> $x=(s,a)$
> $y=R(s)+\gamma\max_{a'}Q(s',a')$

$$
\begin{aligned}
&\text{Initialize neural network randomly as guess of }Q(s,a)\\
&\text{Repeat}
\begin{cases}
\text{Take actions, get }(s,a,R(s),s')\text{ tuples}\\
\text{Store 10,000 most recent }(s,a,R(s),s')\text{ tuples (replay buffer)}\\
\begin{aligned}
&\text{Train neural network:}\\
&\quad\text{Create training set of 10,000 examples using}\\
&\quad{}x=(s,a)\text{ and }y=R(s)+\gamma\max_{a'}Q(s',a')\\
&\quad\text{Train }Q_{new}\text{ such that }Q_{new}(s,a)\approx{y}
\end{aligned}\\
\text{Set }Q=Q_{new}
\end{cases}
\end{aligned}
$$

## Algorithm refinement

### Improved neural network architecture

- Refinement:
	- Input layer $\vec{x}=s$: 8 units 
	- Hidden layer 1: 64 units
	- Hidden layer 2: 64 units
	- Output layer $\vec{y}=\begin{bmatrix}Q(s,nothing)\\Q(s,left)\\Q(s,main)\\Q(s,right)\end{bmatrix}$: 4 units
- Reason:
	- More efficient to train a single neural network to output all four values simultaneously rather than carrying out inference separately for four times

### ε-greedy policy

- Refinement:
	- Exploitation: With probability $1-\epsilon$, take action $a$ that maximizes $Q(s,a)$
	- Exploration: with probability $\epsilon$, take action $a$ randomly
- Possible approach:
	- Start $\epsilon$ high
	- Gradually decrease $\epsilon$
- Reason:
	- Has a small probability to try out different options 
	- Neural network can learn to overcome its own possible preconceptions about what might be a bad option that turns out not to be the case

### Mini-batch

- Refinement:
	- Pick subset of $m’$ (1,000) training examples instead of all $m$ (10,000) examples on every iteration 
- Reason:
	- More efficient [[gradient descent]] calculation and learning algorithm

> Note: can be applied to [[supervised learning]] as well

### Soft update

- Refinement:
	-  When setting $Q=Q_{new}$
	- Set $W=0.01W_{new}+0.99W$
	- Set $B=0.01B_{new}+0.99B$
- Reason:
	- Converge more reliably
	- Less likely to oscillate, divert, or have undesirable properties

> Note: can be applied to supervised learning as well
