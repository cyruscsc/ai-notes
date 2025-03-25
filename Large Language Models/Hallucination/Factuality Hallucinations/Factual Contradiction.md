## Definition

- The generated output contains facts that can be grounded in real-world information, but present contradictions
- Occurs most frequently and arises from diverse sources
- Encompassing the LLM’s capture, storage, and expression of factual knowledge

## Entity-error hallucination

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

## Relation-error hallucination

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
