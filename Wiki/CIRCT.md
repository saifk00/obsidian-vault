#compilers #digital-hardware 
https://circt.llvm.org/
https://circt.llvm.org/docs/Charter/

CIRCT is an LLVM project to provide a [[FIRRTL]] compiler and related tools, i.e. it is the digital hardware equivalent of LLVM's clang.

It operates on [[FIRRTL]], using transforms/analyses from upstream MLIR/LLVM and repurposing them for the hardware domain.

Accelerators must be programmed, but they must also be *built*. MLIR can address both problems.
# Dialects
- `hw`
	- Represents hierarchical concepts - modules, ports, instantiations of modules, etc. 
	- Uses [[mlir-graph-regions]] instead of SSACFGs - this is because values may be referenced before their definition (since the regions describe hardware rather than imperative control flow)
- `seq` and `comb` for sequential and combinational logic
- `llhd` is a lower level hardware dialect that can, among other things, extract timing info and such
- `sv` used for [[system-verilog]] constructs

# References
- [[borup-2022]] discusses CIRCT in the context of [[dynamically-scheduled-high-level-synthesis]]