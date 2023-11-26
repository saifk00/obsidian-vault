# Bayesian Network Factorization
[[bayesian-networks]]
A probability distribution $P$ "factorizes" over a graph $\mathcal{G}$ if it can be expressed as the product
$$
	P(X_1,...,X_n) = \Pi_{i}P(X_i \vert \text{Pa}_{X_i}^{\mathcal{G}})
$$
That is, we could compute the joint probability of the nodes for some assignment by multiplying each of the CPD entries.