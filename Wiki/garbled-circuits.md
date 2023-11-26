Yao's garbled circuits allow us to evaluate arbitrary boolean circuits without revealing each parties input to one another. It works in the 2-party case with arbitrary bit lengths for each parties input. In the 2-party case, A and B have distinct roles. A garbles the circuit and serves as a sender in an [[oblivious-transfer]] protocol, while B evaluates the circuit using A to get labels.

[Protocol](https://www.wikiwand.com/en/Garbled_circuit#Garbled_circuit_protocol)

# Garbling

## Overview
Garbling is the process by which one of the parties (say Alice) obfuscates a circuit so she can safely transfer information *related* to her input value $a$ without actually revealing anything to the receiver.

Essentially, Alice defers the actual computation to Bob, but to compute we need some input; instead of operating on the actual inputs themselves, we let Bob compute a *related* circuit - the crux here is that this related circuit is made in such a way that Alice can recover the actual output were the original circuit computed over the original inputs.

## How it Works
Alice replaces each gate with a truth table. The inputs to the truth table are randomly generated **labels** (usually of a fixed length security parameter $k$). The outputs are the encryption of the output label under the key formed by the concatenation of the input labels. E.g. a row
$$
	X_0^a X_1^b | X_0^c
$$
the output value becomes 

$$
\text{Enc}_{X_0^a || X_1^b}(X_0^c)
$$

^3fe27e

We then perform a permutation of the output column. Why? If we didn't, then Bob would know that, for example, row 1 - which corresponds to $(a, b) = (0, 1)$ - was precisely [[#^3fe27e|this]].
Note that what actually gets *sent* is just the **output column** - if we sent the input columns too then Bob could decrypt every entry! Instead, Bob has to take the input labels he was given and try to decrypt every label (yes, thats exponential!).
### Example: Garbled-ish
To understand why we need to permute the outputs, let's explore what happens if we *didn't*. Say the function was as simple as a 2-input AND gate. First, Alice replaces the truth table with labels and does the encryption:

| a | b | c |
| --- | --- | --- |
| $X_0^a$ | $X_0^b$| $Enc_{X_0^a, X_0^b}(X_0^c)$ |
| $X_0^a$ | $X_1^b$| $Enc_{X_0^a,X_1^b}(X_0^c)$ |
| $X_1^a$ | $X_0^b$| $Enc_{X_1^a,X_0^b}(X_0^c)$ |
| $X_1^a$ | $X_1^b$| $Enc_{X_1^a,X_1^b}(X_1^c)$ |

Now, say we omit the permutation and just send Bob this "garbled-ish" circuit. Furthermore, lets assume that the values are $(a, b) = (1, 1)$.  Alice sends over $X_1^a$ and $X_1^b$ (the latter via [[oblivious-transfer]]). Using these, Bob indexes into the garbled-ish truth table and decrypts the entry in column C corresponding to these labels. He then sends this value $X_1^c$ to Alice who replies with $c=1$ as the output.

Here's the problem: Bob now knows that the value he decrypted, $X_1^c$ , corresponds to $c=1$. Since he obviously knows $b=1$, this means he can infer that $a=1$.

To make this more clear, lets see what happens in the actual garbled situation. Say Alice generates this permutation:

| a | b | c |
| --- | --- | --- |
| $X_0^a$ | $X_0^b$| $Enc_{X_0^a, X_0^b}(X_0^c)$ |
| $X_0^a$ | $X_1^b$| $Enc_{X_0^a,X_1^b}(X_0^c)$ |
| $X_1^a$ | $X_0^b$| $Enc_{X_1^a,X_1^b}(X_1^c)$ |
| $X_1^a$ | $X_1^b$| $Enc_{X_1^a,X_0^b}(X_0^c)$ |

Note that the only difference is that the last two output entries have been swapped. Bob does the same thing as before, this time sending $X_0^c$ to Alice who replies with $c=0$. Now Bob has been foiled: since $b=1$, there's actually two ways he could have computed $c=0$ - either its because $a=0$ (since AND(a, b) = 0 in that case), or its because $a=1$ and the output entry for row $(a, b) = (1, 1)$ was swapped with another one.

## Optimizations
- [[point-and-permute-garbled-circuit]] allows Evan (the evaluator) to avoid having to try decrypting all the output ciphertexts
- [[free-xor]] allows the computation of XOR gates for free (!)
## Questions

**But doesn't Bob need labels too?** Yes - he uses [[oblivious-transfer]] to get labels for *his* input so that he can then pass them through the circuit

**Why can't we just use oblivious transfer then? Isn't Bob effectively transmitting bits of b to Alice in a secure way?** Essentially the question here is why doesn't Bob just 'obliviously transfer' between $f(a, b_0), f(a, b_1)$, and then forward the result back to A? In full generality:
```
Bob: send (b_0, ..., b_m-1) to Alice
Alice: send f(a_0, ... , a_{m-1}, b_0, ..., b_{m-1}) using OT
	- because of OT, Alice doesnt know which output she sent, nor the values of b_0...m-1
Bob: send Alice's reply back
	- because of OT, Alice has no idea which set of inputs this value corresponds to, just that it is the correct one for both their inputs
```
I think the problem here is just that this requires Alice to **precompute** $f(\vec{a}, \vec{b}) \ \  \forall \vec{b} \in \mathbf{2}^{m}$ - an exponential task (if she computed only for the values passed to her, then she would trivially have access to the bits of $\vec{b}$)
## Observations

