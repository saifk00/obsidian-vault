# Overview
Many arguments in statistics take the following syllogistic form:
1. X proportion of F are G
2. I is an F
3. Therefore, the chance that I is a G is X (because of 1)

But take the following example. We wish to know the probability that a blue model-X aircraft will crash. We know the probability of blue planes crashing is 0.2, and the probability of model-X planes crashing is 0.9. We could argue:
1. 20% of blue planes crash
2. the plane is blue
3. Therefore, the chance that the plane crashes is 20%
Or we could argue
1. 90% of model-X planes crash
2. The plane is model-X
3. Therefore, the chance that the plane crashes is 90%

In this example, the **reference classes** are `blue` and `model-X`. The **reference class problem** is this - which is the appropriate reference class to use?

# Origins
Interestingly enough, this problem originates with a guy named John Venn - yes, the Venn of diagram fame is literally named John Venn. He observed that every individual thing can be seen as belonging to an infinite number of classes of things, which leads to the problem of assigning probabilities to individual things.

# Details
[[hajek-2007]] generalizes this problem like so:
> [!quote]
> Let X be a proposition. It seems that there is one unconditional probability of X; but all we find are many conditional probabilities of the form P(X, given A), P(X, given B), P(X, given C), etc. that differ from each other. Moreover, we cannot recover P(X) from these conditional probabilities by the law of total probability, since we likewise lack unconditional probabilities for A, B, C, etc. (and in any case A, B, C, etc. need not form a partition). Relativized to the condition A, X has one probability; relativized to the condition B, it has another; and so on. Yet none of the conditions stands out as being the right one.

One solution we might give is that we consider the "narrowest class" for which we have reliable information. In the plane example, we would pick the class `blue^model-X` supposing there are enough such planes for the metric to make sense. Ignoring minor problems, the crux is that there may be multiple classes that are equally 'narrow':

> [!quote]
> Suppose that there are reliable statistics on the deaths of Englishmen who visit Madeira, and of consumptives who visit Madeira, but not on consumptive Englishmen who visit Madeira. John Smith is a consumptive Englishman visiting Madeira. In which class should we place him?


# Solution
[[hajek-2007]] proposes that we dissolve the reference class problem altogether by accepting [[conditional-probability]] as the fundamental primitive of [[probability-theory]]. He makes an interesting point, and one that I ran into frequently when doing probability in school: 

> For we have now seen more examples of conditional probabilities that cannot be identified with ratios of unconditional probabilities, because the required unconditional probabilities simply don’t exist. Various frequentists could tell us the conditional probability that John Smith will live to age 61, given that he is a consumptive Englishman aged 50. But they could not identify this with the ratio
> $$
\frac{\text{P(John Smith will live to 61 ∩ John Smith is a consumptive Englishman aged 50)}}{\text{P(John Smith is a consumptive Englishman aged 50)}}
 $$ 

What does the denominator even mean? It would make more sense as a conditional - but what condition to use? and those conditions themselves are only referent to another conditional - its conditionals all the way down.

In effect, all probabilities should be conditional if they are to guide our life since our understandings are *always* conditional.