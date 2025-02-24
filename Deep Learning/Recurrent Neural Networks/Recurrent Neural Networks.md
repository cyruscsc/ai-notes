---
aliases:
  - RNNs
---

## Definition

```plaintext
┌─────┐   ┌───────┐   ┌──────┐
│input│ → │network│ → │output│
└─────┘   └───────┘   └──────┘
              ↓
          ┌───────┐   ┌──────┐
          │network│ → │output│
          └───────┘   └──────┘
              ↓
          ┌───────┐   ┌──────┐
          │network│ → │output│
          └───────┘   └──────┘
              ↓
          ┌───────┐   ┌──────┐
          │network│ → │output│
          └───────┘   └──────┘
```

- Where the network uses its own output as input
- Consist of a non-linear structure as opposed to [[Feed-Forward Neural Networks|FNN]]

## Characteristics

- Capable of varying the number of outputs
- Process the input to produce an output, and then continue processing from that point on, producing another output, and repeating as much as necessary
- Helpful in cases where the network deals with sequences and not a single individual object
	- E.g. producing a sequence of words, analyzing videos, translating sentences
