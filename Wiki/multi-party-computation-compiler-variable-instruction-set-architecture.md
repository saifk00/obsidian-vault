#paper
https://eprint.iacr.org/2023/953
# Overview
The authors provide a system to perform [[secure-multi-party-computation]] for arbitrary programs by evaluating the function in an emulated CPU with a variable ISA which itself is evaluated using [[garbled-circuits]]. This is an improvement over works like [[fairplay-a-secure-two-party-computation-system]] because it allows for complex control flow which is normally quite costly to implement in MPC.
# Definitions
- 2PC: 2 party computation; the original formulation of multi-party-computation introduced by Yao ^08bd2c