In an ideal world, we could take some HDL and perform logic synthesis on it independent of the target. A problem arises, however, when the underlying technology (e.g. FPGA library cells) exposes things to the RTL level - crossing a layer of abstraction. For example, in [[verilog]] there is no explicit memory construct - RTL writers just use register arrays from which a compiler must infer memories. But these are often quite inefficient, so fabrication companies provide RTL blocks for SRAM/BRAM etc. which requires an RTL rewrite. But that makes this rewritten RTL tech-dependent, limiting reusability and increasing its complexity.

This is where a hardware *construction* language like [[chisel]] comes in handy. By providing these sorts of abstractions directly in the language, we can abstract their implementation away from the design.

# References
[[izraelevitz-2019]]