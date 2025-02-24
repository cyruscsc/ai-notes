## Defintion

### Randomizing feature choice

- At each node, choose feature to split on from random subset of $k<n$ features
- $n$: number of features available
- Typical choice of $k=\sqrt{n}$
- Randomize the feature choice at each node
- Can cause the set of trees to become more different from each other
- Can result in more accurate prediction in voting

### Intuition

- Even with [[Bagged Decision Tree#Sampling with replacement|sampling with replacement]] procedure, the [[Bagged Decision Tree]] can sometimes ends up using the same splits
- [[Bagged Decision Tree#Sampling with replacement|Sampling with replacement]] procedure and randomized feature choice causes algorithm to explore lot of small changes to data
- Changes are averaged and different decision trees are trained
- Any further little changes to training set are less likely to have huge impact on output
