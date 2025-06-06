## Characteristics

- Enhanced ability to capture information overlap between the model’s [[generation]] and its source
- Initially select target answers from the information units within the LLM’s output 
- Then questions are generated by the question-generation module
- The questions are subsequently used to generate source answers based on the user context
- Finally, the faithfulness of the LLM’s responses is calculated by comparing the matching scores between the source and target answers
