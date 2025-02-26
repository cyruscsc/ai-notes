## Algorithm

- To determine if $KB\models\alpha$
	- Enumerate all possible models
	- If in every model where $KB$ is true, $\alpha$ is true, then $KB$ entails $\alpha$
	- Otherwise, $KB$ does not entail $\alpha$

## Example

$$
\begin{aligned}
P&:\text{It is a Tuesday.}\\
Q&:\text{It is raining.}\\
R&:\text{Harry will go for a run.}\\
\\
KB&:(P\land\neg Q)\rightarrow R\qquad P\qquad \neg R
\end{aligned}
$$

### Query

- $R$
	- Whether $R$ is true or false
	- Does $KB\models R$?

### Possible models

|P|Q|R|KB|
|:-:|:-:|:-:|:-:|
|false|false|false||
|false|false|true||
|false|true|false||
|false|true|true||
|true|false|false||
|true|false|true||
|true|true|false||
|true|true|true||

### Inference

|P|Q|R|KB|
|:-:|:-:|:-:|:-:|
|false|false|false|false|
|false|false|true|false|
|false|true|false|false|
|false|true|true|false|
|true|false|false|false|
|true|false|true|true|
|true|true|false|false|
|true|true|true|false|

- There is only one model where $KB$ is true
- In this model, $R$ is also true
- Therefore, $KB$ entails $R$

## Code samples

> Reference: CS50 AI source code for 1. Knowledge

### Information required

- Knowledge base
	- Used to draw inferences
- A query
	- Or the proposition that we are interested in whether it is entailed by the KB
- Symbols
	- A list of all the symbols (or atomic propositions) used
- Model
	- An assignment of truth and false values to symbols

### Knowledge and logic

```python
from logic import *

# Create new classes representing each proposition
# Each having a name, or a symbol
rain = Symbol("rain")  # It is raining
hagrid = Symbol("hagrid")  # Harry visited Hagrid
dumbledore = Symbol("dumbledore")  # Harry visited Dumbledore

# Save sentences into the KB
# Starting from the "And" logical connective, becasue each proposition represents knowledge that we know to be true
knowledge = And(

  # ¬(It is raining) → (Harry visited Hagrid)
  Implication(Not(rain), hagrid),
  
  # (Harry visited Hagrid) ∨ (Harry visited Dumbledore)
  Or(hagrid, dumbledore),
  
  # ¬(Harry visited Hagrid ∧ Harry visited Dumbledore)
  Not(And(hagrid, dumbledore)),  
  
  # Harry visited Dumbledore
  dumbledore
)
```

### Model checking algorithm

```python
def check_all(knowledge, query, symbols, model):

  # If model has an assignment for each symbol
  if not symbols:

    # If knowledge base is true in model, then query must also be true
    if knowledge.evaluate(model):
      return query.evaluate(model)
    return True
	
    else:

      # Choose one of the remaining unused symbols
      remaining = symbols.copy()
      p = remaining.pop()

      # Create a model where the symbol is true
      model_true = model.copy()
      model_true[p] = True

      # Create a model where the symbol is false
      model_false = model.copy()
      model_false[p] = False

      # Ensure entailment holds in both models
      return(
	    check_all(knowledge, query, remaining, model_true)
		and 
		check_all(knowledge, query, remaining, model_false)
	  )
```

> The logic below might be a little confusing: 
> 1. We start with a list of symbols
> 2. The function is recursive, and every time it calls itself it pops one symbol from the symbols list and generates models from it
> 3. Thus, when the symbols list is empty, we know that we finished generating models with every possible truth assignment of symbols

- The function `check_all` works recursively
	1. Picks one symbol
	2. Creates two models, in one of which the symbol is true and in the other the symbol is false
	3. Calls itself again, now with two models that differ by the truth assignment of this symbol
- The function will keep doing so until all symbols will have been assigned truth-values in the models, leaving the list `symbols` empty
- Once the `symbols` list is empty, in each instance of the function, the function checks whether the KB is true given the model
	- Each instance of the function holds a different model
	- If the KB is true in this model, the function checks whether the query is true
- We are interested only in the models where the KB is true
	- If the KB is false, then the conditions that we know to be true are not occurring in these models, making them irrelevant to our case

