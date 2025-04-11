## Equation

$$
P(sentiment|text)=\frac{P(text)P(text|sentiment)}{P(sentiment)}
$$

## Example with joint probability

> "My grandson loved it!"

$$
\begin{aligned}
P(positive|my,grandson,loved,it)&=\frac{P(positive)P(my,grandson,loved,it|positive)}{P(my,grandson,loved,it)}\\
&=P(positive)P(my,grandson,loved,it|positive)\\
&=P(positive)P(my,grandson,loved,it,positive)\\
&=P(positive)P(my|positive)P(grandson|positive,my)P(loved|positive,my,grandson)P(it|positive,my,grandson,loved)
\end{aligned}
$$

- Calculating this [[joint probability]] is complicated
- The probability of each word is conditioned on the probabilities of the words preceding it


## Example with Naive Bayes

> "My grandson loved it!"

$$
\begin{aligned}
P(positive|my,grandson,loved,it)&=\frac{P(positive)P(my,grandson,loved,it|positive)}{P(my,grandson,loved,it)}\\
&=P(positive)P(my,grandson,loved,it|positive)\\
&=P(positive)P(my,grandson,loved,it,positive)\\
&=P(positive)P(my|positive)P(grandson|positive)P(loved|positive)P(it|positive)
\end{aligned}
$$

- Assume that the probability of each word is independent from other words
- This is not true, but despite this imprecision, [[Naive Bayes]] produces a good sentiment estimate
- Sensitive to words that occur more often in one type of [[Sentence]] than in the other

> The probability of a positive or a negative sentence:
> 
> |Positive|Negative|
> |:-:|:-:|
> |0.49|0.51|
>
> The conditional probabilities of each word occurring in a sentence given that the sentence is positive or negative:
>
> ||Positive|Negative|
> |:-:|:-:|:-:|
> |my|0.30|0.20|
> |grandson|0.01|0.02|
> |loved|0.32|0.08|
> |it|0.30|0.40|

$$
\begin{aligned}
P(positive|my,grandson,loved,it)&=(0.49)(0.30)(0.01)(0.32)(0.30)=0.00014112\\
P(negative|my,grandson,loved,it)&=(0.51)(0.20)(0.02)(0.08)(0.40)=0.00006528
\end{aligned}
$$

- Normalized $P(positive|my,grandson,loved,it)=0.6837$
- Normalized $P(negative|my,grandson,loved,it)=0.3163$



