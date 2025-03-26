---
aliases:
  - RRF
---

## Definition

$$
\mathrm{score}=\sum_{q\in\mathrm{queries}}\frac{1}{k+\mathrm{rank}(q,d)}
$$

> $k$: a constant (typically 60)
> $q$: a query in the set of queries
> $d$: a document
> $\mathrm{rank}(q,d)$: the rank of document $d$ in the results of query $q$

## Approach

- Takes ranked results from multiple query sources
- Assigns a score to each document in each result set
- Scores from all queries are summed for each document
- Documents are then sorted by their combined RRF scores to produce the final ranking

## Advantages

- **Stability across varying score distributions**: RRF focuses on rank positions rather than raw scores, ensuring consistent treatment of results from disparate data sources
- **Resistance to outliers**: By using rankings instead of scores, RRF prevents anomalous values from distorting relevance
- **Consistency in relevance ranking**: RRF favours items that rank highly across diverse query methods, ensuring more reliable relevance ranking
- **No tuning required**: RRF can combine results with different relevance indicators without needing calibration
- **Simplicity and effectiveness**: RRF consistently yields better results than individual systems and other fusion methods like Condorcet Fuse

