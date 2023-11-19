Gibbs sampling is a [[markov-chain-monte-carlo-methods|MCMC]] method for drawing samples from a multivariate probability distribution when we dont know the joint distribution function, but do know the distributions for each variable conditioned on all the other variables.
# In Bayesian Networks
In [[bayesian-networks]] the procedure is as follows.

We draw samples of the whole network - i.e. the sample at time $t$ for a network with $n$ nodes is denoted $\mathbf{x}^t = (x_0^t, x_1^t, ... x_{n-1}^t)$. Let $\mathbf{x}_{-i}^t$ denote the sample at time $t$ with the value for $x_i$ removed. Let $\mathbf{e}$ denote the evidence that was observed.

In each time step, we select one of the nodes $i$ and perform the following update:
$$
\mathbf{x}^t[i] \xleftarrow{} p(x_i | \mathbf{x}_i^{t-1}, \mathbf{e})
$$
That is, we copy over all the values from the previous sample except that we update the $i^\text{th}$ value by sampling it from the distribution conditioned on the values of all the other variables. Some papers say that it helps to choose $i$ randomly in each timestep, but I have not seen any conclusive evidence about this. It is probably sufficient to sample in topological order which seems most natural.

Important note: we have the conditional probability distributions for each node given its *parent nodes*. However, in Gibbs sampling we need to know the distribution conditioned on *all* nodes. This can be determined from the [[markov-blanket]] of a given node. For example, in the following network suppose the evidence is S and W and we wish to find the distribution for C.

![[Pasted image 20231118152639.png]]

We do this as follows:
$$
P(c|r, s, w) = P(c |s, r)
	= P(s,r|c)\frac{P(c)}{P(s,r)}
	= \left(P(s|c) \cdot P(r|c)\right)\frac{P(c)}{P(s|c)P(r|c)P(c) + P(s|\neg c)P(r|\neg c)P(\neg c)} 
$$
where all the values on the right hand side can be determined from the CPDs of C's Markov blanket.