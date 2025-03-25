## Definition

- The [[generation]] stage can encounter significant bottlenecks that may lead to hallucinations

## Contextual awareness

- Involves understanding and effectively utilizing contextual information retrieved

### Noisy context

- The failure in the [[retrieval]] process may inevitably introduce irrelevant information, which will propagate into the [[generation]] stage
- When the generator is not robust enough to these irrelevant retrievals, it will mislead the generator and even introduce hallucinations
- Can train [[Large Language Models|LLMs]] to ignore irrelevant contexts by incorporating irrelevant contexts in training data

### Context conflict

- Situations where contextual knowledge contradicts [[Large Language Models|LLMs]]’ parametric knowledge
- [[Large Language Models|LLMs]] may sometimes exhibit over-confidence, which can bring new challenges to the faithfulness of [[Retrieval Augmented Generation|RAG]] systems
- Can [[Fine-Tuning|fine-tune]] [[Large Language Models|LLMs]] based on counterfactual data augmentation
- Can guide the [[generation]] process by prompting-based strategies

### Context utilization

- [[Large Language Models|LLMs]] can encounter a significant performance degradation due to insufficient utilization of the context
- Especially for information located in the middle of the long context window (lost-in-the-middle phenomenon)
- Can explicitly repeat the question and extract the index of supporting documents before generating answers
- Can incorporate hierarchical and incremental summarization to preserve the salient information and to compress the length of context

## Contextual alignment

- Ensures that LLM outputs faithfully align with relevant context

### Source attribution

- The process by which the model identifies and utilizes the origins of information within its [[generation]] process
- Plan-then-generate: guide the LLM's [[generation]] process
- Generate-then-reflect: empower the LLM to critique its own generation to ensure attributability
- Self-attribution: utilizes model-internal signals to pair context-sensitive answer tokens with retrieved documents

### Faithful decoding

- Improve the models’ ability to generate content that faithfully aligns with contextual information
- Facilitate the integration of contextual spans of arbitrary length into LM generations
- Leverage a faithfulness detector to monitor the beam-search process
