## Definition

- Failures in the [[retrieval]] stage can have serious downstream effects on the [[Retrieval Augmented Generation|RAG]] pipeline, leading to hallucinations

##  User queries

- The specificity and clarity of these queries critically influence the effectiveness of retrieval outcomes

### Retrieval intent

> Retrieved context:
> ```
> At high altitudes, water boils at lower temperatures than at sea level, such as 95°C at elevations above 2,000 meters. This altitude-induced reduction can affect cooking times and methods.
> ```
> Query:
> ```
> What is the boiling point of water at sea level?
> ```
> Response:
> ```
> The boiling point of water at sea level is 95°C.
> ```

- Blind retrieval for queries that do not require external knowledge can counterproductively lead to misleading responses
- Can be addressed by shifting from passive retrieval to [[adaptive retrieval]]
- Decisions can base on [[heuristic]] or self-aware judgement

### Ambiguous queries

> Retrieved context: 
> ```
> The Hennessey Venom GT famously set a speed record by completing a mile on a racetrack in 32 seconds, highlighting its performance in motorsport events.
> ```
> Query: 
> ```
> What’s the record for the fastest mile run on track?
> ```
> Response:
> ```
> The fastest mile on a track was completed in 32 seconds by the Hennessey Venom GT.
> ```

- Ambiguous user queries, containing omission, coreference, and ambiguity, significantly complicate the retrieval system’s ability to fetch precisely relevant information
- A prevalent mitigation strategy is query rewriting, where queries are refined and decontextualized to better match relevant documents

### Complex queries

> Retrieved context:
> ```
> Alexander Fleming, known for his ground-breaking work in discovering penicillin, significantly influenced modern antibiotics. Fleming’s discovery saved countless lives.
> ```
> Query:
> ```
> Which university did the scientist who discovered penicillin graduate from?
> ```
> Response:
> ```
> Alexander Fleming graduated from Oxford University.
> ```

- User queries requiring intensive reasoning or encompassing multiple aspects pose significant challenges to the retrieval system
- Such queries require advanced understanding and decomposition capabilities, which may exceed the current capabilities of the current retrieval methods
- Can be addressed by query [[decomposition]]

## Retrieval sources

- The reliability and scope of retrieval sources are crucial determinants of the efficacy of [[Retrieval Augmented Generation|RAG]] systems
- Modern retrieval models tend to favour LLM-generated content over human-authored content
- Without appropriate intervention, human-generated content may progressively lose its influence within [[Retrieval Augmented Generation|RAG]] systems
- The propensity of [[Large Language Models|LLMs]] to produce factually inaccurate hallucinations exacerbates the reliability issues of retrieval sources
- Can incorporate a quality filter designed to ensure the high quality of the retrieval datastore
- Can equip [[Large Language Models|LLMs]] with the ability to discern and handle information based on its credibility

## Retriever

- When the user query is explicit and the [[retrieval source]] is reliable, the effectiveness of the retrieval process depends crucially on the performance of the retriever

### Chunking 

- Segment the voluminous documents into smaller, more manageable chunks to provide precise and relevant evidence for [[Large Language Models|LLMs]]
- The chunking granularity ranges from documents to paragraphs, even sentences
- Inappropriate retrieval granularity can compromise the semantic integrity and affect the relevance of retrieved information
- Can use semantic chunking instead of fixed-size chunking

### Embedding

- Text chunks are subsequently transformed into vector representation via an embedding model
- Such a representation scheme is supported by the data structure of vector database
- A sub-optimal embedding model may compromise performance, which affects the similarity and matching of chunks to user queries
- Can [[Fine-Tuning|fine-tune]] the embedding models on domain-specific data to enhance retrieval relevance
