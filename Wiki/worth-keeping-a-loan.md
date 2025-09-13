It was my initial assumption that the best thing to do with my student loan is sit on it and use the interest to pay it off. This is actually nonsensical - see the following derivation to determine whether it it worth keeping an (interest-free) loan or paying it off immediately:

Let `M` be the minimum monthly payment on a loan of `L` dollars. You have saved `B` dollars and can stash money somewhere to get a yearly interest rate of `i`. If you keep all the money and invest it, you earn the following amount per month (keeping in mind you must pay `M` monthly as the cost of keeping `L`):

$$
(L+B)*\frac{i}{12}-M
$$
If instead you pay it off, you can omit the `M` payment but have less to invest. In this case you make the following amount per month:
$$
B*\frac{i}{12}
$$
So when is it "worth" keeping the loan. Well, if we determine it 'worth it' if you make more money per month (not *have* more money per month), it is worth it if the former amount is greater than the latter, i.e.
$$
\begin{align}
	(L+B)\frac{i}{12}-M &\gt B\frac{i}{12}\\
	L\frac{i}{12} &\gt M \\
	Li &\gt 12M
\end{align}
$$

For my case, assuming an (optimistic) interest rate of 5% and a loan of 20k, that means the minimum payment would need to be less than $\frac{20,000 * 0.05}{12} = 83$. In my case, the minimum payment is actually 176 - so it is *not* worth it.

When it is advantageous to pay off the loan, you are making the following amount more by doing so:
$$
M - \frac{Li}{12}
$$
For me, thats $92



