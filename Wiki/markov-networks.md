Markov networks are one type of [[probabilistic-graphical-model]].
- [ ] continue reading about markov networks
# Motivation
In the [[pgm-misconception-example]], we find that we cannot capture both the independence properties we intuit with any [[bayesian-networks]]. Intuitively, this is because the relation between the variables is actually *symmetrical* whereas bayesian networks implicitly assume there is directionality to the influence. This notion of symmetry is the core of markov networks.

# Representation
A Markov network is an undirected DAG. The local probability models are called *factors* over the nodes they connect and are denoted $\phi(A, B) : [Val(A) \times Val(B)] \xrightarrow{} \mathbb{R}$. The measure the 'strength' of various combinations of their input nodes. They are *not* probabilities since we want its values to be able to influence the probability of other nodes taking on certain values (think the [[pgm-misconception-example]] - increasing the strengh of ($a^0, b^0$) should affect how likely $d^0$ is).

The joint probability distribution is given by
$$
P(x_0, x_1, ..., x_{n-1}) = \frac{1}{Z}\Pi_i\phi_i(x_{p_i}, x_{j_i})
$$
Where $Z$ is the normalization factor given by the sum of the factor-product over all possible node values.

# Independencies
Two variables are independent given a third if the probability distribution factorizes into a product of two factors like so:
$$
(\vec{X} \perp \vec{Y} \vert \vec{Z}) \iff P(\mathcal{X}) = \phi_1(\vec{X}, \vec{Z})\phi_2(\vec{Y},\vec{Z})
$$
This should make intuitive sense - the factorization on the right implies that X and Z directly interact and Y and Z directly interact, with no direct interaction between X and Y. Thus, knowing Z, should tell us everything we need to know about either of the other variables.

# Parameterization
We need to determine a set of parameters for a given markov network that is able to specify any possible distribution that it induces. The obvious solution - one parameter per entry in each factor - **does not work**: take the trivial case of a complete graph: the number of parameters required to specify any distribution would be $2^n-1$ while the $n\choose{2}$  factors each having 4 parameters can only provide a total of $4{n\choose2}$  parameters which is not enough.

## Factor Product
The product of two factors $\phi_1(X, Y)$ and $\phi_2(Y, Z)$ is a factor $\psi(X, Y, Z) = \phi_1(X, Y) \times \phi_2(Y, Z)$. 

## Gibbs Distribution
A Gibbs distribution is parameterized by a set of factors over arbitrary subsets of variables in the network:
$$\begin{align}
P_\Phi(X_1, ..., X_n) &= \frac{1}{Z}P'_\Phi(X_1, ..., X_n)\\
P'_\Phi &= \phi_1(D_1)\phi_2(D_2),...,\phi_m(D_m)
\end{align}$$
each set $D_i$ introduces direct interactions between its member variables.

## Markov Factorization
Analogous to [[bayesian-network-factorization]], a distribution $P_\Phi$ factorizes over a Markov network $\mathcal{H}$ if each set $D_k$ is a [[complete-graph|complete]] subgraph of $\mathcal{H}$ - thus the factors associated with these sets are also called *clique potentials*. Without losing generality, we can pick $D_k$ to be the [[graph-maximal-cliques]].

## Factor Reduction
When we get evidence, instead of renormalizing the whole distribution after removing inconsistent entries, we can instead just use *reduced* factors. For a factor $\phi(Y)$ and evidence $U=u$ where $U \subseteq Y$, the factor is reduced to $\phi[U=u]$ (or just $\phi[u]$ ) to become a new factor over the scope $Y - U$.
- [ ] Understand this better