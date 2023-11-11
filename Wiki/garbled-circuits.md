Garbled circuits allow us to evaluate arbitrary boolean circuits without revealing each parties input to one another.

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

We then perform a permutation of the output column. Why? If we didn't, then Bob would know that, for example, row 1 - which corresponds to $(a, b) = (0, 1)$ - was precisely [[#^3fe27e|this]]. [[TODO]] I am not sure how this helps Bob to determine $a$ ...


## Questions

**But doesn't Bob need labels too?** Yes - he uses [[oblivious-transfer]] to get labels for *his* input so that he can then pass them through the circuit

**Why can't we just use oblivious transfer then? Isn't Bob effectively transmitting bits of b to Alice in a secure way?** Essentially the question here is why doesn't Bob just 'obliviously transfer' between $f(a, b_0), f(a, b_1)$? Well, its because A also needs to know the result of the function - 