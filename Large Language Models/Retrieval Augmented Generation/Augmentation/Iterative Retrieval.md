## Definition

- Refines the output progressively with multiple rounds of [[retrieval]] and [[generation]]

## Characteristics

- Searches the knowledge base repeatedly based on the initial query and the text generated so far
- Provides a more comprehensive knowledge base for [[Large Language Models|LLMs]]
- Offers additional contextual references through multiple retrieval iterations
- Enhances the robustness of subsequent answer [[generation]] 
- May be affected by semantic discontinuity and the accumulation of irrelevant information
- E.g., ITER-RETGEN

## Process

1. Perform an initial retrieval of relevant documents
2. Generate a response based on the retrieved information
3. Analyze the output for gaps or inaccuracies (feedback loop)
4. Refine the retrieval process using feedback to get better data
5. Repeat the cycle until a satisfactory response is generated or a maximum number of iterations is reached
