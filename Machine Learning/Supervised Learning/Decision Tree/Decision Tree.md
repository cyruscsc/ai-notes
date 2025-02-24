## Topics

- [[Entropy]]
- [[Information Gain]]

## Variations

- [[Regression Tree]]

## Splitting

### Choosing criteria

- Maximize purity (Minimize [[Entropy|impurity]])

### Stopping criteria

- When a node is 100% one class
- When splitting a node will result in the tree exceeding a maximum depth
- When [[Information Gain|information gain]] from additional splits is below a threshold
- When number of examples in a node is below a threshold

## Learning process

1. Start with all examples at the root node
2. Calculate information gain for all possible features
3. Split on the feature with the highest information gain
4. Keep performing recursive splitting until stopping criteria is met

### One hot encoding

- Create $k$ binary features (0 or 1 valued) for a categorical feature with $k$ possible values

## Code examples

```python
def compute_entropy(y):
  """
  Computes the entropy
  Args:
    y (ndarray): Values (0 or 1) of each example at a node
  Returns:
    entropy (float): Entropy at that node
  """
  p_1 = np.sum(y) / len(y)
  is_pure = p_1 == 0 or p_1 == 1
  entropy = 0 if is_pure else -p_1*np.log2(p_1)-(1-p_1)*np.log2(1-p_1)
  return entropy

def split_dataset(X, node_indices, feature):
  """
  Splits the data at the given node into left and right branches
  Args:
    X (ndarray): Data matrix of shape(n_samples, n_features)
    node_indices (list): List containing the active indices. I.e, the samples being considered at this step.
    feature (int): Index of feature to split on
  Returns:
    left_indices (list):  Indices with feature value == 1
    right_indices (list): Indices with feature value == 0
  """
  left_indices = [index for index in node_indices if X[index][feature] == 1]
  right_indices = [index for index in node_indices if X[index][feature] == 0]
  return left_indices, right_indices

def compute_information_gain(X, y, node_indices, feature):
  """
  Computes the information gain of splitting the node on a given feature
  Args:
    X (ndarray): Data matrix of shape(n_samples, n_features)
    y (array like): list or ndarray with n_samples containing the target variable
    node_indices (ndarray): List containing the active indices. I.e, the samples being considered in this step.
    feature (int): Index of feature to split on
  Returns:
    info_gain (float): Information gain computed
  """    
  left_indices, right_indices = split_dataset(X, node_indices, feature)
  X_node, y_node = X[node_indices], y[node_indices]
  X_left, y_left = X[left_indices], y[left_indices]
  X_right, y_right = X[right_indices], y[right_indices]
  h_node = compute_entropy(y_node)
  h_left = compute_entropy(y_left)
  h_right = compute_entropy(y_right)
  w_left = len(X_left) / len(X_node)
  w_right = len(X_right) / len(X_node)
  weighted_h = w_left * h_left + w_right * h_right
  info_gain = h_node - weighted_h
  return info_gain

def get_best_split(X, y, node_indices):   
  """
  Returns the optimal feature and threshold value to split the node data 
  Args:
    X (ndarray): Data matrix of shape(n_samples, n_features)
    y (array like): list or ndarray with n_samples containing the target variable
    node_indices (ndarray): List containing the active indices. I.e, the samples being considered in this step.
  Returns:
    best_feature (int): The index of the best feature to split
  """    
  num_features = X.shape[1]
  is_pure = np.sum(y) == 0 or np.sum(y) == len(y)
  info_gains = [compute_information_gain(X, y, node_indices, feature) for feature in range(num_features)]
  best_feature = -1 if is_pure else np.argmax(info_gains)
  return best_feature
```
