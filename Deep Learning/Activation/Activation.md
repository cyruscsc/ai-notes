## Functions

- [[Step Function]]
- [[Linear Function|Linear]]
- [[Rectified Linear Unit|ReLU]]
- [[Sigmoid Function|Sigmoid]]
- [[Softmax Function|Softmax]]

## Choosing activation function

### Hidden layer

- Most common choice: [[Rectified Linear Unit|ReLU]]
- Another choice: [[Sigmoid Function|Sigmoid]]

### Output layer

- Depend on desired value of $y$
- Binary classification: 
  - $0<y<1$, use [[Sigmoid Function|Sigmoid]]
- Multiclass classification:
  - Multiple $y$ values, use [[Softmax Function|Softmax]]
- Regression: 
  - $y\le0\text{ or }y\ge0$, use [[Linear Function|Linear]]
  - $y\ge0$, use [[Rectified Linear Unit|ReLU]]

## Python Implementation

### Regression

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
  Dense(units=25, activation="relu"),
  Dense(untis=15, activation="relu"),
  Dense(units=1, activation="linear")
])
```

### Binary classification

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
  Dense(units=25, activation="relu"),
  Dense(untis=15, activation="relu"),
  Dense(units=1, activation="sigmoid")
])
```

### Multiclass classification

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.losses import SparseCategoricalCrossentropy

# Steps to reduce numerical roundoff errors:
# 1.   Set output layer to use linear activation function
# 2.   Put softmax function into specification of loss function
# 3.1. Take output z values and map it through
# 3.2. Map through softmax function to get predicted probability
# Also work for logistic regression

# Specify the model
model = Sequential([
  Dense(units=25, activation="sigmoid"),
  Dense(untis=15, activation="sigmoid"),
  Dense(units=10, activation="linear") # step 1
])
# Specify loss and cost
model.compile(
  loss=SparseCategoricalCrossentropy(from_logits=True) # step 2
)
# Train on data to minimize cost
model.fit(X, y, epochs=100)
# Make prediction
logits = model(x) # step 3.1, output z_1 to z_10 instead of a_1 to a_10
f_x = tf.nn.softmax(logits) # step 3.2
```
