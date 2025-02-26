## Definition

- Model's ability to adapt to new, previously unseen data, drawn from same distribution as one used to create model

## Overfitting

- High variance
- Fits training set extremely well
	- $J_{train}$ is low
	- $J_{cv}$ is high
	- $J_{train}\gg{J_{cv}}$
- Fits the training data so well that it fails to generalize to other data sets

## Underfitting

- High bias
- Does not fit training set well
	- $J_{train}$ is high
	- $J_{cv}$ is high
	- $J_{train}\thickapprox{J_{cv}}$

## Addressing overfitting

- Collect more data
- [[Feature Selection]]
- [[Regularization]]
