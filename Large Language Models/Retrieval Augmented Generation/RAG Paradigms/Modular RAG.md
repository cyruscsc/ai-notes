## Characteristics

- Builds upon the foundational principles of [[Naive RAG]] and [[Advanced RAG]]
- Offers enhanced adaptability and versatility compared to [[Naive RAG]] and [[Advanced RAG]] by allowing module substitution or reconfiguration to address specific challenges
- Enhances applicability across different tasks by integrating new modules or adjusting interaction flow among existing ones
- Incorporates diverse strategies for improving its components
	- E.g., adding a search module for similarity searches, refining the retriever through fine-tuning
- Restructured [[Retrieval Augmented Generation|RAG]] modules and rearranged [[Retrieval Augmented Generation|RAG]] pipelines have been introduced to tackle specific challenges

## Modules

### Search module

- Adapts to specific scenarios
- Enables direct searches across various data sources using LLM-generated code and query languages
	- E.g., search engines, databases, and knowledge graphs

### RAG-Fusion

- Addresses traditional search limitations by employing a [[multi-query]] strategy
- Expands user queries into diverse perspectives
- Utilizes parallel vector searches and intelligent re-ranking to uncover both explicit and transformative knowledge
- See [[RAG-Fusion]]

### Memory module

- Leverages the LLM’s memory to guide [[retrieval]]
- Creates an unbounded memory pool that aligns the text more closely with data distribution through iterative self-enhancement

### Routing

- Navigates through diverse data sources
- Select the optimal pathway for a query, whether it involves summarization, specific database searches, or merging different information streams
- See [[Routing]]

### Predict module

- Reduces redundancy and noise by generating context directly through the LLM
- Ensures relevance and accuracy

### Task adapter module

- Tailors RAG to various downstream tasks
- Automates prompt retrieval for zero-shot inputs
- Creates task-specific retrievers through few-shot query generation

## Patterns

### Integrating modules

- **Rewrite-Retrieve-Read**: Leverages the LLM’s capabilities to refine retrieval queries through a rewriting module and a LM-feedback mechanism to update rewriting model
- **Generate-Read**: Replaces traditional retrieval with LLM-generated content
- **Recite-Read**: Emphasizes retrieval from model weights, enhancing the model’s ability to handle knowledge-intensive tasks
- **Hybrid retrieval strategies**: Integrate keyword, semantic, and vector searches to cater to diverse queries
- **Sub-queries**, **[[Hypothetical Document EmbeddingsHyDE|HyDE]]**: Improve retrieval relevance by focusing on embedding similarities between generated answers and real documents

### Adjusting module arrangement

- **Demonstrate-Search-Predict (DSP)**, **ITER-RETGEN**: Use module outputs to bolster another module’s functionality
- **FLARE**, **Self-RAG**: Transcend the fixed [[Retrieval Augmented Generation|RAG]] [[retrieval]] process by evaluating the necessity of retrieval based on different scenarios
