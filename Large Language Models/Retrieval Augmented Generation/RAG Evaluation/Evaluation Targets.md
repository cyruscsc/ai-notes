## Retrieval

### Relevance

- Query ↔ relevant documents
- Evaluates how well the retrieved documents match the information needed expressed in the query
- Measures the precision and specificity of the retrieval process

### Accuracy

- Relevant documents ↔ documents candidates
- Assesses how accurate the retrieved documents are in comparison to a set of candidate documents. 
- Measures the system’s ability to identify and score relevant documents higher than less relevant or irrelevant ones

## Generation

### Relevance

- Response ↔ query

- Measures how well the generated response aligns with the intent and content of the initial query
- Ensures that the response is related to the query topic and meets the query’s specific requirements

### Faithfulness

- Response ↔ relevant documents
- Evaluates if the generated response accurately reflects the information contained within the relevant documents
- Measures the consistency between generated content and the source documents

### Correctness

- Response ↔ sample response
- Measures the accuracy of the generated response against a sample response, which serves as a ground truth
- Checks if the response is correct in terms of factual information and appropriate in the context of the query

## Additional requirements

### Latency

- Measures how quickly the system can find information and respond, crucial for user experience

### Diversity

- Checks if the system retrieves a variety of relevant documents and generates diverse responses

### Noise robustness

- Assesses how well the system handles irrelevant information without affecting response quality

### Negative rejection

- Gauges the system’s ability to refrain from providing a response when the available information is insufficient

### Counterfactual robustness

- Evaluates the system’s capacity to identify and disregard incorrect information, even when alerted about potential misinformation
