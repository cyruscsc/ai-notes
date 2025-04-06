## Tools

|Framework|Targets|Retrieval|Generation|
|:-:|:-:|:-:|:-:|
|TruEra RAG Triad|Relevance<br>Groundedness|LLM|LLM|
|LangChain Bench|Accuracy<br>Faithfulness<br>Execution time<br>Embeddings cosine distance|Accuracy|LLM|
|Databricks Eval|Correctness<br>Readability<br>Comprehensiveness|-|LLM|

## Benchmarks

|Framework|Targets|Datasets|Retrieval|Generation|
|:-:|:-:|:-:|:-:|:-:|
|RAGAs|Relevance<br>Faithfulness|WikiEval|LLM|Cosine similarity<br>LLM|
|RECALL|Correctness<br>Robustness|EventKG<br>UJ|-|BLEU<br>ROUGE-L|
|ARES|Relevance<br>Faithfulness|NQ<br>Hotpot<br>FEVER<br>WoW<br>MultiRC<br>ReCoRD|LLM + classifier|LLM + classifier|
|RGB|Faithfulness<br>Noise robustness<br>Negative rejection<br>Counterfactual robustness|Generated|-|Accuracy|
|MultiHop-RAG|Accuracy<br>Correctness|Generated|MAP<br>MRR<br>Hit@k|LLM|
|CRUD-RAG|Create<br>Read<br>Update<br>Delete|Generated<br>UHGEval|-|ROUGE<br>BLEU<br>RAGQuestEval|
|MedRAG|Accuracy|MIRAGE|-|Accuracy|
|FeB4RAG|Faithfulness<br>Correctness<br>Clarity<br>Coverage|FeB4RAG<br>BEIR|-|Human|
|CDQA|Accuracy|Generated|-|F1|
|DomainRAG|Correctness<br>Faithfulness<br>Noise robustness<br>Structural output|Generated|-|F1<br>Exact-Match<br>ROUGE-L<br>LLM|
|ReEval|Hallucination|RealTimeQA<br>NQ|-|F1<br>Exact-Match<br>Human<br>LLM|
