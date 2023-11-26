The problem of points is a classic [[probability-theory]] problem. Two players, R and S, play a game where each player has an equal chance of winning each round. Each contributes equally to a prize pot, and the first player to get to N wins takes the pot. Suppose they are interrupted at round K - how should they distribute the pot?

This problem was solved in 1654 by [[fermat]] and [[pascal]] (who had correspondence around this time). In so doing, they laid out the principles that led to modern [[probability-theory]], including [[expected-value]].

# Fermat's Solution
Fermat proposed this: suppose that R needs $r$ rounds to win, and S needs $s$ rounds. The maximum number of rounds left in the game is $r + s - 1$ . Why? suppose without loss of generality that $s \geq r$. In the worst case, S wins $(s-1)$ rounds and R wins $r$ rounds, for a total of $r+s-1$ rounds.

Suppose that all futures have equal length (that is, they keep playing even after one player has won). Then it is clear that each of $2^{r+s-1}$ futures is equally likely. The [[odds]] are given by the number of futures where R would win vs. S, and the players should divide the pot proportional to this value.

# Pascal's Addition
To Fermat's solution, Pascal adds an argument as to why this is 'fair' using one of the earliest examples of [[proof-by-induction]].

Suppose that, after the interruption, the players play one more round. Suppose (inductive hypothesis) that we have a fair division for that extra round. Based on who wins, this extra round has one of two fair divisions (by inductive hyp.). Since it is equally likely who wins, the fair division for *this* round is the average of the two future fair divisions.

We can construct the solution thusly - the base cases are those in which one of the players wins: $\forall_{r < N} (N, r)$  and $\forall_{s<N}(s, N)$. We can then construct the fair divisions for the adjacent cases (where R or S is one round short of winning), and continue until we get to the given state. This is sort of a [[dynamic-programming]] algorithm, which could also be implemented recursively.