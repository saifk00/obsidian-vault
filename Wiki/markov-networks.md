Markov networks are one type of [[probabilistic-graphical-model]].
#todo continue reading about markov networks
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