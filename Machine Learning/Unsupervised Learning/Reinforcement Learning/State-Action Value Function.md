---
aliases:
  - Q function
---

## Definition

> From CS50 AI by Harvard

$$
Q(s,a)\leftarrow Q(s,a)+\alpha((r+\gamma \max_{a’}Q(s’,a’))-Q(s,a))
$$

> $\alpha$: learning coefficient
> $s$: state
> $a$: action
> $r$: reward
> $\gamma$: value of the future reward estimate

- A model of reinforcement learning
- $Q(s,a)$ outputs an estimate of the value of taking action $a$ in state $s$

## Approach

> From CS50 AI by Harvard

- Starts with all estimated values equal to 0 ($Q(s,a)=0$, for all $s$, $a$) 
- When an action is taken and a reward is received, the function does two things:
	- Estimates the value of $Q(s,a)$ based on current reward and expected future rewards
	- Updates $Q(s,a)$ to take into account both the old estimate and the new estimate
- New estimate = reward + future reward estimate
- Future reward estimate = estimate of the action in the new state that will bring to the highest reward


## Bellman equation

> From Machine Learning by DeepLearning.AI

$$
\begin{aligned}
Q(s,a)&=\text{Return, if}
\begin{cases}
\text{start in state }s\\
\text{take action }a\text{ once}\\
\text{behave optimally after that}
\end{cases}\\
&=R(s)+\gamma\max_{a’}Q(s’,a’)
\end{aligned}
$$
> $s$: current state
> $a$: current action
> $s’$: state after taking action $a$
> $a’$: action to be taken in state $s’$
> $R(s)$: reward of current state

## Intuition 

> From Machine Learning by DeepLearning.AI

- The best possible return from state $s$ is $\max_{a}Q(s,a)$
- The best possible action in state $s$ is the action $a$ that gives $\max_{a}Q(s,a)$
- $\pi(s)=a,\text{ where }\max_{a}Q(s,a)$

$$
\begin{aligned}
\text{Sequence of rewards}&=R_1+\gamma{}R_2+\gamma^2R_3+\gamma^3R_4+\cdots\\
Q(s,a)&=R_1+\gamma[R_2+\gamma{}R_3+\gamma^2R_4+\cdots]
\end{aligned}
$$
> $R1$: reward gotten right away 
> $\gamma[R_2+\gamma{}R_3+\gamma^2R_4+\cdots]$: return from behaving optimally starting from $s’$

## Stochastic environment

> From Machine Learning by DeepLearning.AI

$$
\begin{aligned}
Q(s,a)&=\text{Expected return}\\
&=Average(R_1+\gamma{}R_2+\gamma^2R_3+\gamma^3R_4+\cdots)\\
&=R(s)+\gamma{}E[\max_{a’}Q(s’,a’)]
\end{aligned}
$$
> $s$: current state
> $a$: current action
> $s’$: state after taking action $a$
> $a’$: action to be taken in state $s’$
> $R(s)$: reward of current state

- Goal: choose a policy $\pi(s)=a$ that tells what action $a$ to take in state $s$ so as to maximize the expected return
