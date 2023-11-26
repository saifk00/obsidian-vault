- [ ] refine this note
# Overview
A [[bayesian-probability|Bayesian]] Network is one type of [[probabilistic-graphical-model]]. It represents a situation as a [[directed-acyclic-graph]] where nodes are [[random-variables]] and edges represent [[statistical-conditional-independence| conditional dependencies]].

Bayesian networks are useful for modelling situations where we measure some *outcome*, and want to reason backwards to one of several *causes* of that outcome. For example:
- Given some symptoms, find the likelihood that the patient has a specific disease
- Given a speech signal, find the likelihood that the sound was one of several [[phoneme]]s

# Representing Bayesian Networks
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
# Notation
The notation used is due to [[koller-2009]].
- $\mathcal{G}$: A Bayesian network structure containing $n$ nodes:
- $\mathcal{I}_l(\mathcal{G})$: The set of local independencies encoded by a Bayesian Network
# Reasoning in Bayesian Networks
There are several patterns of reasoning that involve bayesian networks. Take the [[student-bayesian-network]] as reference. The three patterns are as follows
## Causal Reasoning
Causal reasoning is when we observe 'upstream' factors and want to predict their 'downstream' results. For example, given a student's letter result (whether they got a reference letter or not), we want to reason backwards to the causes - their intelligence and the difficulty of the class.
## Evidential Reasoning
Evidential reasoning is when we reason from the effects (e.g. the grades and letter results) to the causes (e.g. an individual's intelligence).
## Inter-causal Reasoning

^2a2f88

Intercausal reasoning is when we find that different causes of the same effect interact. For example, the student's grade is influenced both by their Intelligence and the Difficulty of the course. If, by observing the SAT score, we gain some information on their Intelligence (say, that it was high despite a low grade), we also learn something about the Difficulty - namely, that it is more likely to be hard.

One concrete example is 'explaining away' a cause. For example, if we have {fever, sore throat}, getting diagnosed with the flu might 'explain away' the potential cause mononucleosis.
# Independencies in Bayesian Networks

^2cea7f

Intuitively, a node's parents "shield" it from all other causal variables. That is, given a node's parents, a node is independent of all the nodes 'upstream' of those parents. Note, however, that a node is *not* independent of its descendants. Formally, the set of local independencies encoded by a Bayesian network is:
$$
\mathcal{I}_l(\mathcal{G}) = \{(X_i\perp\text{NonDescendants}|\text{Pa}_{X_i}^{\mathcal{G}}) \vert X_i \in \mathcal{G}\}
$$
# Factorization and I-Maps
[[bayesian-network-i-maps]]
[[bayesian-network-factorization]]

# d-Separation
We know that for a distribution $P$ and a bayesian network $\mathcal{G}$ that factorizes over it, $G$ is an I-map of $P$ and thus $\mathcal{I}(\mathcal{G}) \subseteq \mathcal{I}(P)$. We know the left hand side from [[#^2cea7f| Independencies in Bayesian Networks]], but there are other independencies that we know about $P$ if it factorizes over $\mathcal{G}$.

To grok this, we visualize influence as 'flowing' from one node to the next, through each node on the path. A trail between two nodes $X$ and $Y$ is 'active' if influence can flow from $X$ to $Y$. If a node along the path is observed, the path becomes inactive - *except* in the collider case. As in [[#^2a2f88|Intercausal Reasoning]], influence can flow between two *causes* if their common effect (or one of its descendants) is observed. So, for a path to continue to be active in the presence of this so-called 'collider' structure, the node $Z$ or one of its descendants must be observed:
![[Pasted image 20231121223426.png]]

d-separation, or 'directed separation' formalizes this notion of 'influence flowing'. Two nodes $X$ and $Y$ are d-separated given evidence $\vec{Z}$ if there is no active trail between them. Then, the set of independencies in $\mathcal{G}$ is actually generalized to:
$$
	\mathcal{I}(\mathcal{G}) = \{(X \perp Y \vert Z) \vert \text{ d-sep}(X,Y \vert \vec{Z}) \}
$$
Note that this subsumes the local independencies $\mathcal{I_l}(\mathcal{G})$ where Y are the non-descendants of X and Z are the parents of X in $\mathcal{G}$. Thus, it is called the set of *global* Markov independencies. **Note**: as much as we would like it to, in general, $\mathcal{I}(\mathcal{G}) \neq \mathcal{I}(P)$.

# I-Equivalence
The set $\mathcal{I}(\mathcal{G})$ is not uniquely identified by graph structure. In particular, for any given distribution $P$ there may be many graph structures that encode the same independencies but vary in the directionality of their edges. This is very important since the *causal interpretation* of a network varies based on the edge directions.

If two graphs are I-equivalent, any distribution that factorizes over one of them factorizes over the other. The set of all graphs over $\mathcal{X}$ (the set of variables in the distribution) is partitioned into mutually exclusive I-equivalence *classes*. 

If two graphs have the same *skeleton*, and the same v-structures, they are I-equivalent. This implication does not go the other way - there are graphs with different v-structures that are I-equivalent.
# Related
[[naive-bayes-models]] - a class of Bayesian networks that was once used for medical diagnosis
# References
[[koller-2009]] sec. 3