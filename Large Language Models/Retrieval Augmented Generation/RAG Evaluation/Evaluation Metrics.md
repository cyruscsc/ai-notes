## Retrieval metrics

### Non-rank based metrics

- **Accuracy**: the proportion of true results among the total number of cases examined
- **[[Precision]]**: the fraction of relevant instances among the retrieved instances
- **[[Recall]]@k**: the fraction of relevant instances that have been retrieved over the total amount of relevant cases, considering only the top k results

### Rank based metrics

- **Mean Reciprocal Rank (MRR)**: the average of the reciprocal ranks of the first correct answer for a set of queries
- **Mean Average Precision (MAP)**: the mean of the average precision scores for each query

## Generation metrics

- **ROUGE**: 
	- Recall-Oriented Understudy for Gisting Evaluation
	- A set of metrics designed to evaluate the quality of summaries by comparing them to human-generated reference summaries
- **BLEU**: 
	- Bilingual Evaluation Understudy
	- A metric for evaluating the quality of machine-translated text against one or more reference translations
- **BertScore**: Leverages the contextual embedding from pre-trained transformers like BERT to evaluate the semantic similarity between generated text and reference text
- **LLM as a Judge**: [[Large Language Models|LLMs]] are used to score the generated text based on criteria such as coherence, relevance, and fluency
