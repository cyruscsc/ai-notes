## Pre-training

- While facilitating efficient training, [[Full Language Modelling|Causal Language Modelling]] inherently limits the ability to capture intricate contextual dependencies, potentially increasing risks for the emergence of [[hallucination]]
- [[Large Language Models|LLMs]] can occasionally exhibit unpredictable reasoning hallucinations spanning both long-range and short-range dependencies, which potentially arise from the limitations of soft [[Attention]]
- The phenomenon of exposure bias has been a longstanding and serious contribution to hallucinations, resulting from the disparity between training and inference in the auto-regressive generative model

## Fine-tuning

- Over-fitting on new factual knowledge encourages LLMs prone to fabricating content, amplifying the risk of hallucinations
- Traditional SFT methods typically force models to complete each response, without allowing them to accurately express uncertainty

## RLHF

- LLM’s activations encapsulate an internal belief related to the truthfulness of its generated statements
- Misalignment can occasionally arise between these internal beliefs and the generated outputs even when [[Large Language Models|LLMs]] are refined with human feedback
- Models trained via [[Reinforcement Learning from Human Feedback|RLHF]] exhibit pronounced behaviours of pandering to user opinions