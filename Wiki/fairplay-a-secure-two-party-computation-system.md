http://www.pinkas.net/PAPERS/MNPS.pdf
# Overview
The authors present a practical system to achieve [[secure-multi-party-computation]] in the two-party case. The compile a high level description of a function (in a language called **SFDL** - secure function definition language) into a boolean circuit (described in a language called **SHDL** - secure hardware definition language) which can then be evaluated [[garbled-circuits]].
# Observations
- The authors state that the compiled circuit cannot use registers, loops, and 'must use every gate only once'. I think this essentially boils down to 'no sequential logic'
- The SHDL is evaluated *in software* - this allows them to have simple optimization goals; namely, minimize the number of gates in the circuit
# Ideas
- Why do the authors use a custom HDL as the backend? Maybe we could integrate this into [[CIRCT]] to provide even more flexibility
