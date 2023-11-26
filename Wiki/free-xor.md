In [[garbled-circuits]], the free XOR technique allows us to evaluate XOR gates for free (i.e. no decryption necessary). Normally, output labels $W^0$ and $W^1$ are random. Instead, in the free XOR technique we do the following:
- Generate a random 'label mask' $R \xleftarrow{} \{0,1\}^L$  where $L$ is the length of the labels. This is one value for the whole circuit
- For each gate, pick its $W^0$ label at random, and set its $W^1=W^0 \oplus R$

Then, for the XOR gates $k$ with input gates $i, j$, set
$$\begin{align}
	W_k^0 &= W_i^0 \oplus W_j^0\\
	W_k^1 &= W_k^0 \oplus R
\end{align}$$
We can then evaluate an XOR gate by taking the labels computed for the input wires and simply XORing them. Basically, because of the way we set up the labels (W^0 random and W^1 = W^0 xor R), we can compute the correct output label of the XOR gate *without* gaining any information on the input labels. This is because it works out no matter what inputs the labels correspond to.
$$\begin{align}
	W_i^0 \oplus W_j^0 &= W_k^0 \\
	W_i^0 \oplus W_j^1 &= W_i^0 \oplus (W_j^0 \oplus R) = (W_i^0 \oplus W_j^0)\oplus R = W_k^0 \oplus R = W_k^1\\
	W_i^1 \oplus W_j^0 &= (W_i^0 \oplus R) \oplus W_j^0 = (W_i^0 \oplus W_j^0)\oplus R = W_k^0 \oplus R = W_k^1\\
	W_i^1 \oplus W_j^1 &= (W_i^0 \oplus R) \oplus (W_j^0 \oplus R) = W_k^0
\end{align}$$
The evaluator does *not* know which bit values each of the labels corresponds to. They only know that it is *correct* according to the garbling rules. That is, no matter which of the four pairs of input labels they got, the output label they compute using XOR is the correct one for that situation.
# Discussion

For an XOR gate, the table normally looks like

| i     | j     | k                         |
| ----- | ----- | ------------------------- |
| W_i^0 | W_j^0 | Enc_{W_i^0, W_j^0}(W_k^0) |
| W_i^0 | W_j^1 | Enc_{W_i^0, W_j^1}(W_k^1) |
| W_i^1 | W_j^0 | Enc_{W_i^1, W_j^0}(W_k^1) |
| W_i^1 | W_j^1 | Enc_{W_i^1, W_j^1}(W_k^0) |

Using [[point-and-permute-garbled-circuit]] the evaluator can select the right ciphertext, but still needs to decrypt that one. Free XOR allows them to skip that step altogether and immediately get the right output label which can be fed into the next gate.