# Conditional Independence
Intuitively, two events $\alpha$ and $\beta$ are conditionally [[probabilistic-independence|independent]] given $\gamma$ if $\gamma$ gives us all the information relevant in $\beta$ that we need to know the probability of $\alpha$ (and vice versa). Consider this example:
- $\alpha$ - whether student X was admitted to MIT
- $\beta$ - whether student X was admitted to Stanford
- $\gamma$ - student X's GPA
We might reasonably assume that the GPA captures all the relevant information for us to deduce X's chances of getting into MIT even if we know whether they were admitted to Stanford (or vice versa).

# Formal Definition
We denote two events as conditionally independent given a third event using $\alpha \perp \beta \vert \gamma$. The following is true:
$$
(\alpha \perp \beta \vert \gamma) \iff P(\alpha\beta\vert\gamma) = P(\alpha\vert\gamma)P(\beta\vert\gamma) 
$$


# References
[[koller-2009]] sec 2.1.4.2