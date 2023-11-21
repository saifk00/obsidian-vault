#statistics

A [[bayesian-probability|Bayesian]] Network is one type of [[probabilistic-graphical-model]]. It represents a situation as a [[directed-acyclic-graph]] where nodes are [[random-variables]] and edges represent [[statistical-conditional-independence| conditional dependencies]].

Bayesian networks are useful for modelling situations where we measure some *outcome*, and want to reason backwards to one of several *causes* of that outcome. For example:
- Given some symptoms, find the likelihood that the patient has a specific disease
- Given a speech signal, find the likelihood that the sound was one of several [[phoneme]]s

# Representation
Benefits of the Bayesian Network representation
- Explicitly representing the joint distribution over $n$ variables is difficult
	- Computationally, expensive to manipulate and store
		- [[idea]]: if this is true, then it is also expensive to compute the entire joint distribution and then marginalize it to compute a probability given some evidence. This is why [[swiftstat]] computes the estimate *iteratively*
	- Cognitively, impossible to have experts provide all those values; they don't correspond to any intuitive events
- Gives us fewer parameters to work with - this is *good* because it reduces the amount of data required to *learn* the network
	- For example, if the $n$ random variables are the outcomes of coin flips, we would normally need $2^n$ probability values to fully specify the joint distribution. However, if we know the outcomes are marginally independent, we can assign a parameter $\theta_{x_i}$ to each coin and compute the probability as $P_{\vec{x}} = \Pi{\theta_{x_i}}$ ; thus only requiring $n$ parameters.
- Modularity
	- Adding a new variable only requires specifying its CPD and connections to existing nodes; with explicit representation we must recompute all $2^n-1$ values
There are two ways of viewing a Bayesian network
1. A data structure that tells you how to compute the joint distribution using the factors (edges)
2. A way to represent the set of conditional independence assumptions about a distribution
We can view a Bayesian network as comprising two components
1. The *structure* which conveys our understanding of how the variables relate to one another through conditional independencies
2. The *local probability models* - i.e. the CPDs, which convey our understanding of a particular influence
# Inference

# Related
[[naive-bayes-models]] - a class of Bayesian networks that was once used for medical diagnosis

# References
[[koller-2009]] sec. 3