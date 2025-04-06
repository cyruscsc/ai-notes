## Evaluation targets

### Downstream tasks

- Focus on the execution in specific downstream tasks
- Employ established metrics suitable to the tasks at hand
- E.g., EM, [[F1 score]], accuracy

### Retrieval quality

- Determine the effectiveness of the context sourced by the retriever component
- Employ standard metrics from the domains of search engines, recommendation systems, and information retrieval systems
- E.g., hit rate, MRR, NDCG

### Generation quality

- Focus on the generator’s capacity to synthesize coherent and relevant answers from the retrieved context
- Can be categorized based on the content’s objectives
	- **Labeled content**: focuses on the accuracy of the information produced by the model
	- **Unlabeled content**: encompasses the faithfulness, relevance, and non-harmfulness of the generated answers

## Evaluation aspects

### Quality scores

- **Context relevance**: evaluates the precision and specificity of the retrieved context
- **Answer faithfulness**: ensures that the generated answers remain true to the retrieved context
- **Answer relevance**: requires that the generated answers are directly pertinent to the posed questions

### Required abilities

- **Noise robustness**: appraises the model’s capability to manage noise documents that are question-related but lack substantive information
- **Negative rejection**: assesses the model’s discernment in refraining from responding when the retrieved documents do not contain the necessary knowledge to answer a question
- **Information integration**: evaluates the model’s proficiency in synthesizing information from multiple documents to address complex questions
- **Counterfactual robustness**: tests the model’s ability to recognize and disregard known inaccuracies within documents, even when instructed about potential misinformation
