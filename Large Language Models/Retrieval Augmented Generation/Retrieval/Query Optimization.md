## Characteristics

- The question may be complex, and the language may not be well-organized
- Language models often struggle when dealing with specialized vocabulary or ambiguous abbreviations with multiple meanings

## Query expansion

- Expands a single query into multiple queries enriches the content of the query
- Provides further context to address any lack of specific nuances

### Multi-query

- Expand queries via LLMs by employing prompt engineering
- Queries can then be executed in parallel
- See [[Multi-Query]]

### Sub-query

- Generate the necessary sub-questions to contextualize and fully answer the original question
- A complex question can be decomposed into a series of simpler sub-questions using the [[least-to-most prompting]] method

### Chain-of-verification (CoVe)

- The expanded queries undergo validation by LLM to achieve the effect of reducing [[hallucination]]
- Validated expanded queries typically exhibit higher reliability

## Query transformation

- Retrieve chunks based on a transformed query instead of the user’s original query
- Prompt LLM to rewrite the queries
- Can also prompt LLM to generate a query based on the original query for subsequent [[retrieval]]

## Query routing

- Route to distinct [[Retrieval Augmented Generation|RAG]] pipeline based on varying queries
- See [[Routing]]

### Metadata router/filter

- Extract keywords (entity) from the query
- Filter based on the keywords and metadata within the chunks to narrow down the search scope

### Semantic router

- Leverage the semantic information of the query
