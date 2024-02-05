Supposing that when you bulk you gain a certain % as fat and the rest as muscle, and that you lose a certain % of fat as you cut, I created the following formulas to determine the length of a cut and bulk to achieve the desired results.

'Desired results' being (1) gaining a certain amount of muscle, and (2) achieving a certain body fat percentage. These seem to be reasonable goals.

Constants:
- `p` - your current body fat percentage (e.g. 0.2)
- `W` - your current weight
- `B` - the amount you will aim to gain per day (should be in the range of 0.5/7 for relatively lean gains)
- `L` - the amount you will aim to lose per day (should be in the range of 1% of body weight; anything drastic removes the linearity assumptions)
- `m` - the percentage of your gains you expect to come from muscle
- `f` - the percentage of your cut you expect to lose as fat
For my estimates, I use the following
```
p=0.2
W=150
B=0.5/7
L=1/7
m=0.5
f=0.9
```
Then, you can compute `n_b` and `n_c` - the number of days you need to bulk and cut respectively - using the following linear system:
$$\begin{align}
W\cdot(F-p)&=B\cdot(1-m-F)n_b-Lfn_c\\
M &= Bmn_b + L(f-1)n_c
\end{align}$$
Personally, I just plug the constants into excel and numerically invert them.