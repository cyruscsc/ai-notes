## Characteristics

- Skips some of the recursive computations that are decidedly unfavorable
- No need to further investigate the actions that can bring the opponent to get to a better score than the already established action

## Example

```mermaid
flowchart TD
    A[/4\]

    B1[\4/]
    B2[\≤3/]
    B3[\≤2/]

    C1[/4\]
    C2[/8\]
    C3[/5\]

    C4[/9\]
    C5[/3\]
    C6[/x\]

    C7[/2\]
    C8[/x\]
    C9[/x\]

    A-->B1
    A-->B2
    A-->B3

    B1-->C1
    B1-->C2
    B1-->C3

    B2-->C4
    B2-->C5
    B2-->C6

    B3-->C7
    B3-->C8
    B3-->C9
```