## Hallucination from data

### Misinformation and biases

- Misinformation and biases may present within [[pre-training]] data and may inadvertently be amplified
- Manifest as imitative falsehood and the reinforcement of societal biases

### Knowledge boundary

- The inability of [[Large Language Models|LLMs]] to memorize all factual knowledge encountered during [[pre-training]], especially the less frequent long-tail knowledge
- The intrinsic boundary of the [[pre-training]] data itself, which does not include rapidly evolving world knowledge or content restricted by copyright laws

### Inferior alignment data

- LLMs struggle to acquire new knowledge in [[fine-tuning]] effectively
- There is a correlation between the acquisition of new knowledge through [[fine-tuning]] and increased hallucinations

## Hallucination from training

### Pre-training

- While facilitating efficient training, [[Full Language Modelling|Causal Language Modelling]] inherently limits the ability to capture intricate contextual dependencies, potentially increasing risks for the emergence of [[hallucination]]
- [[Large Language Models|LLMs]] can occasionally exhibit unpredictable reasoning hallucinations spanning both long-range and short-range dependencies, which potentially arise from the limitations of soft [[attention]]
- The phenomenon of exposure bias has been a longstanding and serious contribution to hallucinations, resulting from the disparity between training and inference in the auto-regressive generative model

### Fine-tuning

- Over-fitting on new factual knowledge encourages LLMs prone to fabricating content, amplifying the risk of hallucinations
- Traditional SFT methods typically force models to complete each response, without allowing them to accurately express uncertainty

### RLHF

- LLM’s activations encapsulate an internal belief related to the truthfulness of its generated statements
- Misalignment can occasionally arise between these internal beliefs and the generated outputs even when [[Large Language Models|LLMs]] are refined with human feedback
- Models trained via [[Reinforcement Learning from Human Feedback|RLHF]] exhibit pronounced behaviours of pandering to user opinions

## Hallucination from inference

### Imperfect decoding strategies

- An elevation in the sampling temperature results in a more uniform token probability distribution, increasing the likelihood of sampling tokens with lower frequencies from the tail of the distribution
- The heightened tendency to sample infrequently occurring tokens exacerbates the risk of hallucinations

### Over-confidence

- Stems from an excessive focus on the partially generated content, often prioritizing fluency at the expense of faithfully adhering to the source context
- Language models often exhibit a localized focus within their [[attention]] mechanisms, giving priority to nearby words and resulting in a notable deficit in context attention

### Softmax bottleneck

- The majority of language models utilize a [[Softmax Function|softmax]] layer that operates on the final layer’s representation within the language model, in conjunction with a word embedding, to compute the ultimate probability associated with word prediction
- The employment of [[Softmax Function|softmax]] in tandem with distributed word embeddings constrains the expressivity of the output probability distributions given the context which prevents LMs from outputting the desired distribution

### Reasoning failure

- Effective utilization of knowledge is inextricably linked with reasoning capabilities
- Even if the LLM possesses the necessary knowledge, it may struggle to produce accurate results if multiple associations exist between questions, due to its limitations in reasoning
