## Definition

### Basic

$$
\begin{gathered}
P\lor Q\\
\neg P\\
-----\\
Q
\end{gathered}
$$

- If one of two atomic propositions in an Or proposition is false, the other has to be true
- E.g. "Ron is in the Great Hall" Or "Hermione is in the library" + "Ron is not in the Great Hall" = "Hermione is in the library"

### Further generalized

$$
\begin{gathered}
P\lor Q\\
\neg P\lor R\\
-----\\
Q\lor R
\end{gathered}
$$

- E.g. "Ron is in the Great Hall" Or "Hermione is in the library" + "Ron is not in the Great Hall" Or "Harry is sleeping" = "Hermione is in the library" Or "Harry is sleeping"

## Complementary literals

- Two of the same atomic propositions where one is negated and the other is not
- E.g. $P$ and $\neg P$
- Allow us to generate new sentences through inferences by resolution
- Inference algorithms locate complementary literals to generate new knowledge
