## Random initialization

- Random permutation with uniform probability
- e.g. `1, 3, 5, 2, 6, 7, 4, 9, 10, 8` (traveling salesman problem, 10 cities)

### Nearest neighbour greedy approach

- Select first city `i` at random
- Then choose city `j` which minimizes distance between `i` and `j`
- Repeat selecting `j` with `i` to be the last selected city
- Iterate through this process until all cities are added in the route
