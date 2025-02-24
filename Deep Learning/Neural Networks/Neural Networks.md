## Concepts

- [[Perceptron]]
- [[Multilayer Neural Networks]]
- [[Deep Neural Networks]]

## Definition

- Model mathematical functions that map inputs to outputs based on the structure and parameters of the network
- Allows for learning he network's parameters based on data

## Terminology

- **Neuron** = takes input, computes formula, outputs activation $a$
- **Layer** = grouping of neurons which takes similar features as input and output activations $\vec{a}$
- **Input layer** = layer 0
- **Hidden layer** = layer 1 to layer n-1
- **Output layer** = layer n
- **Inference** = prediction
- **Binary cross entropy** = cross entropy function for binary classification 
- **Epochs** = number of iterations in [[Gradient Descent]]

## Notation

- $a$ = activation value
- $g$ = activation function

## Model function

$$
a^{[l]}_j=g(\vec{w}^{[l]}_j\cdot\vec{a}^{[l-1]}+b^{[l]}_j)
$$
> $a^{[l]}_j$: activation value of layer $l$, unit (neuron) $j$
> $\vec{a}^{[l-1]}$: vector of activation values (output) from previous layer
> $\vec{w}^{[l]}_j,b^{[l]}_j$: parameters of layer $l$, unit (neuron) $j$

- If network has $s_{in}$ units in a layer and $s_{out}$ units in the next layer, then 
	- $W$ will be a matrix of dimension $s_{in} \times s_{out}$
	- $\vec{b}$ will be a vector with $s_{out}$ elements


## Neural network training

### Create model

- Specify how to compute output given input $x$ and parameters $w,b$

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
  Dense(units=25, activation="sigmoid"),
  Dense(untis=15, activation="sigmoid"),
  Dense(units=1, activation="sigmoid")
])
```

### Loss and cost functions

- Specify loss and cost

```python
from tensorflow.keras.losses import BinaryCrossentropy

model.compile(loss=BinaryCrossentropy())
```

### Gradient descent

- Train on data to minimize cost

```python
model.fit(X, y, epochs=100)
```

## Code examples

### NumPy

```python
import numpy as np

def dense(a_in, W, b):
  """
  Computes dense layer
  Args:
    a_in (ndarray (n, )) : Data, 1 example
    W    (ndarray (n,j)) : Weight matrix, n features per unit, j units
    b    (ndarray (j, )) : bias vector, j units
  Returns:
    a_out (ndarray (j,)) : j units|
  """
  units = W.shape[1]
  a_out = np.zeros(units)
  for j in range(units):
    w = W[:,j]
    z = np.dot(w, a_in) + b[j]
    a_out[j] = g(z)
  return a_out

def sequential(x, W1, b1, W2, b2):
  a1 = dense(x, W1, b1)
  a2 = dense(a1, W2, b2)
  return a2

def predict(X, W1, b1, W2, b2):
  m = X.shape[0]
  p = np.zeros((m, 1))
  for i in range(m):
    p[i,0] = sequential(X[i], W1, b1, W2, b2)
  return p
```

### TensorFlow

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
  Dense(units=3, activation="sigmoid"),
  Dense(units=1, activation="sigmoid")
])
model.compile(loss=BinaryCrossentropy())
model.fit(x, y)
model.predict(x_new)
```

## Playground

> [Tensorflow Playground](https://playground.tensorflow.org/)