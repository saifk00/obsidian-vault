https://llvm.org/devmtg/2021-11/slides/2021-CIRCT-LiftingHardwareDevOutOfThe20thCentury.pdf
# Overview
An introduction to the motivation behind the [[CIRCT]] project.
# Key Takeaways
- While there are FOSS tools becoming available for HW design (yosys, verilator, icarus, etc.) - none of them are tackling the **representational issue** - SystemVerilog is simply insufficient
- The authors mention that designs become "a mess of scripts, TCL, vendor-specific files, and duct-tape" - something that we kind of take for granted, but it [[need-not-be-this-way]]!
- CIRCT aims to do for hardware design what LLVM did for software compilers
- There are some key differences between a potential HW IR and traditional imperative IR for software (e.g. combinational loops, cant represent dataflow as a DAG)
- Separate compilation - we'd like to compile each module separately the same way we do with object files; a symbol table now contains a module's signals!