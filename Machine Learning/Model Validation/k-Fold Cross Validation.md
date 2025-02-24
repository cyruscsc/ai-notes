## Approach

- Divide the data into $k$ sets
- Run the training $k$ times
- Each time leaving out one dataset and using it as a test set
- End up with $k$ different evaluations of our mode
- Can be averaged to get an estimate of how our model generalizes without losing any data