## Definition

- Rules for how nodes should be rearranged
- Mitigate problems associated with weak locality in rearranging nodes

## Swapping

```
target: 3, 7
before: 1-2-3-4-5-6-7-8
after: 1-2-7-4-5-6-3-8
```

- Swapping two non-adjacent nodes leads to low locality
- Results in reconnecting more than two nodes

## Inversion operator

```
target: 3, 7
before: 1-2-3-4-5-6-7-8
after: 1-2-7-6-5-4-3-8
```

- Strong locality
- Results in rearranging only two nodes

## 2-opt operator

```
target: AE, CD
before: A-B-C-D-E-A
after: A-B-C-E-D-A
```

- Remove two non-self and non-adjacent edges
- Reconnect the open nodes in different order
- Same principles can be used to design n-opt operator
