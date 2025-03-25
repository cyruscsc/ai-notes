## Characteristics

- [[Retrieval Augmented Generation|RAG]] relies on external knowledge to enhance LLMs
- The type of [[retrieval]] source and the granularity of retrieval units both affect the final generation results

## Data structure

### Unstructured data

- Most widely used retrieval source mainly gathered from corpus, such as text
- Common sources include encyclopedic data, cross-lingual text and domain specific data
- E.g., ODQA, HotpotQA

### Semi-structured data

- Data that contains a combination of text and table information, such as PDF
- Text splitting processes may inadvertently separate tables, leading to data corruption during retrieval
- Incorporating tables into the data can complicate semantic similarity searches
- E.g., Text-2-SQL, TableGPT

### Structured data

- Typically verified and can provide more precise information, such as knowledge graphs
- Requires additional effort to build, validate, and maintain structured databases
- E.g., KnowledGPT, G-Retriever

### LLMs-generated content

- Exploits LLMs’ internal knowledge
- Addresses the limitations of external auxiliary information in [[Retrieval Augmented Generation|RAG]]
- LLM-generated contexts often contain more accurate answers due to better alignment with the pre-training objectives of causal language modeling
- E.g. SKR, GenRead

## Retrieval granularity

- Choosing the appropriate retrieval granularity during inference can improve the retrieval and downstream task performance of dense retrievers
- For texts, granularity includes token, phrase, sentence, proposition, chunks, and document
- For Knowledge graphs, granularity includes entity, triplet, and sub-graph

### Coarse-grained retrieval unit

- Theoretically can provide more relevant information for the problem
- But may also contain redundant content, which could distract the retriever and language models in downstream tasks

### Fine-grained retrieval unit

- Increases the burden of retrieval
- Does not guarantee semantic integrity and meeting the required knowledge
