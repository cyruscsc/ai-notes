## Definition

- Recommend items based on features of user and item to find good match

## Notation

$v^{(j)}_u$: vector of numbers computed from user features $x^{(j)}_u$

$v^{(i)}_m$: vector of numbers computed from movie features $x^{(i)}_m$

> Note: $x^{(j)}_u$ and $x^{(i)}_m$ can be different in size

## Model function

$$
\begin{aligned}
\text{Regression:}
&&f(x)&=v^{(j)}_u\cdot{v}^{(i)}_m\\
\text{Classification:}
&&f(x)&=g(v^{(j)}_u\cdot{v}^{(i)}_m)=\frac{1}{1+e^{-(v^{(j)}_u\cdot{v}^{(i)}_m)}}
\end{aligned}
$$
> $g$: [[Logistic Regression#Sigmoid logistic function|sigmoid function]]
> Note: $v^{(j)}_u$ and $v^{(i)}_m$ have to be of same size

## Neural network architecture

- Use two networks to compute $v_u$ from $x_u$ and  $v_m$ from $x_m$
- Input layers
  - Can have different number of units
  - $x_u$ and $x_m$ can be of different size
- Hidden layers
  - Can have different number of layers
  - Can have different number of units per layer
- Output layers
  - Must have same number of units
  - $v_u$ and $v_m$ have to be of same size
- Use [[#Model function|model function]] to make predictions from $v_u$ and $v_m$

## Cost function

$$
J=\sum_{(i,j):r(i,j)=1}(f(x)-y^{(i,j)})^2+\text{neural network regularization term}
$$

### Finding related items

- Find item $k$ similar to item $i$ = find item $k$ with $\min\|v^{(k)}_m-v^{(i)}_m\|^2$ from item $i$
$$
\text{Squared distance }\|v^{(k)}_m-v^{(i)}_m\|^2=\sum_{l=1}^n(v^{(k)}_{m_l}-v^{(i)}_{m_l})^2
$$
- Can be pre-computed ahead of time

## Recommending from large catalogue

### Retrieval 

- Generate large list of plausible item candidates
	- For each of the last 10 movies watched by the user, find 10 most similar movies
	- For most visited 3 genres, find the top 10 movies
	- Top 20 movies in the country
- Combine retrieved items into list
	- Remove duplicates
	- Remove items already watched / purchased

### Ranking

- Take list retrieved and rank using learned model
  - Feed user features and movie features to the neural network
  - Compute predicted rating for each user-movie pair
    - $v_m$ for all movies can be computed in advance
    - Compute $v_u$ a single time and make predictions with $v_m$
- Display ranked items to user

### Performance-speed tradeoff

- Retrieving more items results in better performance, but slower recommendations
- To analyze / optimize the tradeoff
	- Carry out offline experiments
	- See if retrieving additional items results in more relevant recommendations ($\uparrow\hat{y}^{(i,j)}$)

## Code examples

### Neural network architecture

```python
import tensorflow as tf

num_outputs = 32
tf.random.set_seed(1)
user_NN = tf.keras.models.Sequential([
  tf.keras.layers.Dense(units=256, activation="relu"),
  tf.keras.layers.Dense(units=128, activation="relu"),
  tf.keras.layers.Dense(units=num_outputs, activation="linear"),
])
item_NN = tf.keras.models.Sequential([
  tf.keras.layers.Dense(units=256, activation="relu"),
  tf.keras.layers.Dense(units=128, activation="relu"),
  tf.keras.layers.Dense(units=num_outputs, activation="linear"),
])
# create the user input and point to the base network
input_user = tf.keras.layers.Input(shape=(num_user_features))
vu = user_NN(input_user)
vu = tf.linalg.l2_normalize(vu, axis=1)
# create the item input and point to the base network
input_item = tf.keras.layers.Input(shape=(num_item_features))
vm = item_NN(input_item)
vm = tf.linalg.l2_normalize(vm, axis=1)
# compute the dot product of the two vectors vu and vm
output = tf.keras.layers.Dot(axes=1)([vu, vm])
# specify the inputs and output of the model
model = tf.keras.Model([input_user, input_item], output)
# specify the cost function and optimizer
cost_fn = tf.keras.losses.MeanSquaredError()
opt = keras.optimizers.Adam(learning_rate=0.01)
# compile and fit the model
model.compile(optimizer=opt, loss=cost_fn)
model.fit([user_train[:, u_s:], item_train[:, i_s:]], y_train, epochs=30)
```
