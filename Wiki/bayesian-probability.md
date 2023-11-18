#statistics #philosophy

Bayesian probability, also known as **subjectivism**, is one possible interpretation of probability in the [[philosophy-of-probability]]. Also called evidential probability, it is closely tied to [[epistemic-probability]] in that probability values under this theory can be assign to any proposition whatsoever. The value is interpreted as a quantification of the degree of plausibility.

# Methodology
- [[random-variables]] are used to model all *sources* of uncertainty ([[stochastic-probability|stochastic]] or [[epistemic-probability|epistemic]])
- a [[bayesian-prior]] distribution that represents available information
- sequential application of [[bayes-theorem]] to update the [[bayesian-prior]]
- the use of hypotheses in the form of probability queries over the set of random variables, where the probability represents the degree of belief.

# History
[[bayes|Thomas Bayes]] himself only introduced a special case of what is now known as [[bayes-theorem]]. It was expanded upon by [[laplace]] - to whom we credit the fromulation of what is now known as Bayesian probability. A resurgence of interest in Bayesian probability occured in the 190s with the discovery of [[markov-chain-monte-carlo-methods]] and the proliferation of computers, which lowered the computational load of Bayesian updating.


# Radical Subjectivism
All subjectivists regard probabilities as *rationality constraints* on degrees of belief. *Radical* subjectivists such as [[de-finetti]] and others regard them as the **only** valid constraints. It says nothing in particular about the values themselves, just that in so far as they justify your beliefs, they must be coherent - if probability for A is greater than that of B, you must believe A more than B.

## Constrained Subjectivism
There are various formulations of this - I will present them as [[hajek-2007]] did. In this theory, there are 'agents' and 'experts' who guide the agents' beliefs through their probability functions:
$$
P(A|pr(A)=x)=x
$$
i.e. that if the expert probability assignment of $A$ is $x$, then the "agent" will regard the probability of $A$ as $x$. For example, you may consider your local weather station the 'expert' about the weather, in which case you will follow their probability function for the chance of rain tomorrow.
