## Imperfect decoding strategies

- An elevation in the sampling temperature results in a more uniform token probability distribution, increasing the likelihood of sampling tokens with lower frequencies from the tail of the distribution
- The heightened tendency to sample infrequently occurring tokens exacerbates the risk of hallucinations

## Over-confidence

- Stems from an excessive focus on the partially generated content, often prioritizing fluency at the expense of faithfully adhering to the source context
- Language models often exhibit a localized focus within their [[attention]] mechanisms, giving priority to nearby words and resulting in a notable deficit in context attention

## Softmax bottleneck

- The majority of language models utilize a [[Softmax Function|softmax]] layer that operates on the final layer’s representation within the language model, in conjunction with a word embedding, to compute the ultimate probability associated with word prediction
- The employment of [[Softmax Function|softmax]] in tandem with distributed word embeddings constrains the expressivity of the output probability distributions given the context which prevents LMs from outputting the desired distribution

## Reasoning failure

- Effective utilization of knowledge is inextricably linked with reasoning capabilities
- Even if the LLM possesses the necessary knowledge, it may struggle to produce accurate results if multiple associations exist between questions, due to its limitations in reasoning
