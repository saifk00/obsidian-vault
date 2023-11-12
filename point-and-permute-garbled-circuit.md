#cryptography

Point-and-permute is a technique used in [[garbled-circuits]] to save Evan (the evaluator) from trying to decrypt all 4 ciphertexts of a garbled circuit. Recall that, normally, he must do this because he has no idea which input labels were used to encrypt each of the output labels in a garbled circuit (he receives only the output column).

1. Each wire $w$ is associated with two *permute* bits $p^0$, $p^1$
2. For each wire with labels $W_i = \{W_0, W_1\}$, generate a random $r$, $p_i = i \oplus r$
3. For each gate $k$ with input wires $W^{k_1}_i$ and $W^{k_2}_j$ , the output index is $2p^{k_2}_j + p^{k_1}_j$
```python
def permute_bit(wire: Wire):
	r = random_bit()
	p[0] = r
	p[1] = !r
	return p

def garble():
	for gate: (Wire, Wire) in Gates:
		permute[gate.wireA] = permute_bit(gate.wireA)
		permute[gate.wireB] = permute_bit(gate.wireB)
		# generate the output label

def evaluate_gate(gate, L_G):
	L_E = OT(E.value)
	pg = L_G[-1]
	pe = L_E[-1]
	ind = 2*pe + pg
	decrypt(gate[ind], L_G[:-1]||L_E[:-1])
```
