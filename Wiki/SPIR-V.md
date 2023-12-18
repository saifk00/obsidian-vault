https://www.lei.chat/posts/compilers-and-irs-llvm-ir-spirv-and-mlir/
- [[opencl-spirv-llvm-history]] - SPIR was originally meant to pin LLVM IR at specific versions, so that drivers could rely on that format (if you want code to be supported by driver X, you would target the right SPIR version to ensure compatibility). This was necessitated by [[llvm-weak-compatibility]]
- SPIR-V was deemed worth developing for the compatibility guarnatees not provided by [[llvm]] IR
	- Also SPIR-V supports [[spir-v-extensions]] in a standard, manageable way
- "hardware drivers update much less frequently than software toolchains" - this is why stability and compatibility are key features of SPIR-V
- Designed for fast consumption by *device drivers*
- 