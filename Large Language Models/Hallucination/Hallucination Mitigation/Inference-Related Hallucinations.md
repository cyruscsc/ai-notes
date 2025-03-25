## Factuality enhanced decoding

- Improve the reliability of outputs from LLMs by prioritizing the factuality of the information they generate
- Focus on aligning model outputs closely with established real-world facts, thereby minimizing the risk of disseminating false or misleading information

### Factuality decoding

- Dynamically adjust the nucleus probability throughout sentence generation based on decay factors and lower boundaries
- Adjust activations along the truth-correlated direction during inference
- Dynamically select and contrasts logits from different layers to refine decoding factuality

### Post-editing decoding

- Harness the self-correction capabilities of [[Large Language Models|LLMs]] to refine the originally generated content without relying on an external knowledge base
- Leverage the inherent ability of [[Large Language Models|LLMs]] to first generate factual knowledge and then refine the response until it aligns consistently with the provided background knowledge

## Faithfulness enhanced decoding

- Prioritize alignment with the provided context and also emphasizes enhancing the consistency within the generated content

### Context consistency

- Encourage the LLM to focus more on contextual information rather than over-rely on prior knowledge
- Detect contextual hallucinations at different levels and then refine the generated response
- Overcome the [[Softmax Function|softmax]] bottleneck that constrains the expression of diversity and faithful representations

### Logical consistency

- The unfaithfulness issue lies in the inconsistencies in the context information obtained by the CoT and the answer
- Enhance the self-consistency in chain-of-thought
- Eliminate reasoning shortcuts that derive answers without considering the rationale
- Reduce surface-level copying and prevent missed reasoning steps
- Align the LLM towards preferring correct reasoning chains over counterfactual chains
- Encourage the LLM to reason faithfully over the reasoning steps using a counterfactual and causal preference objective
