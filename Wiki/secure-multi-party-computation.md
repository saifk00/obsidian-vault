Multi-party computation: the idea here is that there are N parties who each have some private information $n_i$. Each would like to know the value of some function $f(n_0, n_1, ... n_{n-1})$ without revealing its $n_i$ to the other parties (as a result, each party $i$ knows nothing but $(n_i, f)$). Furthermore, they would like to do this *without* needing a trusted third party.

There is some variation in how exactly we model the trust among the parties themselves.

- [[millionaires-problem]] - a classic example of MPC
- [[garbled-circuits]] - a way to evaluate boolean circuits in MPC
