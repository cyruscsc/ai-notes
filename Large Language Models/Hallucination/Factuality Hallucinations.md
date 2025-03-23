## Definition

- The generation of outputs that are inconsistent with real-world facts or unverifiable

## Factual contradiction

- The generated output contains facts that can be grounded in real-world information, but present contradictions
- Occurs most frequently and arises from diverse sources
- Encompassing the LLM’s capture, storage, and expression of factual knowledge

### Entity-error hallucination

> Instruction:
> ```
> What are Thomas Edison’s main contributions to science and technology?
> ```
> Response:
> ```
> Thomas Edison developed the first practical telephone and invented the light bulb.
> ```

- The generated output contains erroneous entities
- Conflicts with the real fact that it was `Alexander Graham Bell`

### Relation-error hallucination

> Instruction:
> ```
> What are Thomas Edison’s main contributions to science and technology?
> ```
> Response:
> ```
> Thomas Edison developed the first practical telephone and invented the light bulb.
> ```

- The generated output contains wrong relations between entities
- The fact is that he improved upon existing designs and did not invent it

## Factual fabrication

- The generated output contains facts that are unverifiable against established real-world knowledge

### Unverifiability hallucination

> Instruction:
> ```
> What are the major environmental impacts of the construction of the Eiffel Tower?
> ```
> Response:
> ```
> The construction of the Eiffel Tower in 1889 led to the extinction of the Parisian tiger, a species that played a crucial role in the region’s ecosystem. Additionally, it is widely recognized as the event that sparked the global green architecture movement.
> ```

- The generated output contains statements that are entirely non-existent or cannot be verified using available sources
- `Parisian tiger` is a species that does not exist
- The claim cannot be substantiated by any historical or biological record

### Overclaim hallucination

> Instruction:
> ```
> What are the major environmental impacts of the construction of the Eiffel Tower?
> ```
> Response:
> ```
> The construction of the Eiffel Tower in 1889 led to the extinction of the Parisian tiger, a species that played a crucial role in the region’s ecosystem. Additionally, it is widely recognized as the event that sparked the global green architecture movement.
> ```

- The generated output contains claims that lack universal validity due to subjective biases
- This is an overclaim, as there is no broad consensus or substantial evidence to support the statement
