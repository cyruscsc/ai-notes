## Notation

$c^{(i)}$ = index of cluster ($1,2,\ldots,K$) to which example $x^{(i)}$ is currently assigned

$\mu_k$ = cluster centroid $k$

$\mu_{c^{(i)}}$ = cluster centroid of cluster to which example $x^{(i)}$ has been assigned

## Approach

- Maps all data points in a space, and then randomly places $k$ cluster centers in the space
- Each cluster gets assigned all the points that are closest to its center than to any other center
- In an iterative process, the cluster center moves to the middle of all these points
- Points are reassigned again to the clusters whose centers are now closest to them
- When, after repeating the process, each point remains in the same cluster it was before, we have reached an equilibrium and the algorithm is over

## Algorithm

$$
\begin{aligned}
&\text{Initiate }K\text{ cluster centroids}\\
&\text{Repeat}
\begin{cases}
\text{for }i=1\text{ to }m\text{, }\\
\begin{aligned}
\quad{c}^{(i)}&\coloneqq\text{index of cluster centroid closet to }x^{(i)}\\
&\coloneqq\min_k\parallel{x}^{(i)}-\mu_k\parallel \end{aligned}\\
\text{for }k=1\text{ to }K\text{, }\\
\begin{aligned}
\quad\mu_k&\coloneqq\text{average of points in cluster }k\\
&\coloneqq\frac{1}{n}\sum_{i=1}^nx^{(i)}
\end{aligned}
\end{cases}
\end{aligned}
$$ 
### Intuition

1. Randomly pick two points to be cluster centroids
2. Assign each data points to its closet centroid
3. Recompute centroids (move to average locations of corresponding data points)
4. Repeat step 2 and step 3 until convergence (no more changes to locations of centroids and assigned data points)

## Cost function 

$$
J(c^{(i)},\ldots,c^{(m)},\mu_1,\ldots,\mu_k)
=\frac{1}{m}\sum_{i=1}^m\parallel{x}^{(i)}-\mu_{c^{(i)}}\parallel^2
$$

- Also known as **distortion cost function**

## Initializing k-means

- For $i=1$ to $100$ (between 50-1000):
  1. Randomly initialize k-means
  2. Run k-means to get $c^{(1)},\ldots,c^{(m)},\mu_1,\ldots,\mu_k$
  3. Compute cost function $J(c^{(i)},\ldots,c^{(m)},\mu_1,\ldots,\mu_k)$
- Pick set of clusters that gave lowest cost $J$

### Random initialization

1. Choose $K<m$ (number of cluster centroids < number of examples)
2. Randomly pick $K$ training examples
3. Set $\mu_1,\ldots,\mu_k$ equal to these $K$ examples

## Choosing number of clusters

### Elbow method

1. Run k-means with various values of $K$
2. Plot distortion cost function $J$ as function of number of clusters
3. Choose the elbow (the point where decrement of $J$ becomes more slowly than before)

#### Downside

- Sometimes the right number of clusters is ambiguous
- In many cases, $J$ decreases smoothly without a clear elbow 

### Performance on downstream purpose

- Evaluate k-means based on how well it performs on the downstream purpose

#### T-shirt size example

1. Possible valid values of $K$
   - $K=3$ (S, M, L)
   - $K=5$ (XS, S, M, L, XL)
2. Make decision based on what make sense for the business
   - Tradeoff between how t-shirts will fit and costs
   - $K=3$: $\downarrow$ t-shirts fit, $\downarrow$ manufacturing and shipping costs
   - $K=5$: $\uparrow$ t-shirts fit, $\uparrow$ manufacturing and shipping costs

### Inappropriate technique

- Choose $K$ so as to minimize cost function $J$
- Almost always choose the largest possible value of $K$
- Having more clusters almost always reduces cost function $J$

## Code examples

### k-means algorithm

```python
import numpy as np

def run_kMeans(X, initial_centroids, max_iters=10):
  """
  Runs the K-Means algorithm on data matrix X, where each row of X is a single example
  """
  # Initialize values
  m, n = X.shape
  K = initial_centroids.shape[0]
  centroids = initial_centroids
  idx = np.zeros(m)
  # Run K-Means
  for i in range(max_iters):
    # Output progress
    print("K-Means iteration %d/%d" % (i, max_iters-1))
    # For each example in X, assign it to the closest centroid
    idx = find_closest_centroids(X, centroids)
    # Given the memberships, compute new centroids
    centroids = compute_centroids(X, idx, K)
  return centroids, idx
```

### Random initialization

```python
import numpy as np

def kMeans_init_centroids(X, K):
  """
  This function initializes K centroids that are to be used in K-Means on the dataset X
  Args:
    X (ndarray)        : data points 
    K (int)            : number of centroids/clusters
  Returns:
    centroids (ndarray): initialized centroids
  """
  # Randomly reorder the indices of examples
  randidx = np.random.permutation(X.shape[0])
  # Take the first K examples as centroids
  centroids = X[randidx[:K]]
  return centroids
```

### Find the closet centroids

```python
import numpy as np

def find_closest_centroids(X, centroids):
  """
  Computes the centroid memberships for every example
  Args:
    X (ndarray)        : (m, n) input values      
    centroids (ndarray): (K, n) centroids
  Returns:
    idx (array_like)   : (m,) closest centroids
  """
  # Set K
  K = centroids.shape[0]
  # You need to return the following variables correctly
  idx = np.zeros(X.shape[0], dtype=int)
  for i in range(len(idx)):
    distances = []
    for j in range(K):
      norm_ij = np.linalg.norm(X[i] - centroids[j]) ** 2
      distances.append(norm_ij)
    idx[i] = np.argmin(distances)
  return idx
```

### Compute centroids

```python
import numpy as np

def compute_centroids(X, idx, K):
  """
  Returns the new centroids by computing the means of the 
  data points assigned to each centroid.
  Args:
    X (ndarray)        : (m, n) Data points
    idx (ndarray)      : (m,) Array containing index of closest centroid for each example in X. Concretely, idx[i] contains the index of the centroid closest to example i
    K (int)            : number of centroids
  Returns:
    centroids (ndarray): (K, n) New centroids computed
  """
  # Useful variables
  m, n = X.shape
  # You need to return the following variables correctly
  centroids = np.zeros((K, n))
  for k in range(K):
    centroids[k] = np.mean(X[idx == k], axis=0)
  return centroids
```

