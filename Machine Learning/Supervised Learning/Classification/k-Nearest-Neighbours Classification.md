## Characteristics

- Assigns value to the variable in question based on the most frequent value of the $k$ nearest neighbours
- It is up to the programmer to decide what $k$ is

## Limitations

- Using a naive approach, the algorithm will have to measure the distance of every single point to the point in question, which is computationally expensive
- Can be sped up by using data structures that enable finding neighbours more quickly or by pruning irrelevant observations