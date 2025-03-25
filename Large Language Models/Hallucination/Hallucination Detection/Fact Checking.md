## Definition

- Extract and verify the correctness of the independent factual statements within the model’s outputs against trusted knowledge sources

## External retrieval 

- Decompose the generation content into atomic facts
- Compute the percentage supported by reliable knowledge sources

## Internal checking

- Generate verification questions for a draft response
- Leverage [[Large Language Models|LLMs]]' parametric knowledge to assess the consistency of the answer against the original response
- As [[Large Language Models|LLMs]] are not inherently reliable factual databases, solely relying on LLMs’ parametric knowledge for fact-checking may result in inaccurate assessments
