# Altera OpenCL Platform

Initially released in 2012, Altera had an implementation of OpenCL for its FPGAs known as the *Altera SDK for OpenCL* or **AOCL**. As an [[opencl|OpenCL 1.0]]-compliant implementation, it provided a runtime and a compiler. The compiler, called the **Altera Offline Compiler** `aoc` (yes, offline - not OpenCL - check the original 2014 getting started guide for proof).

It also provided a utility called `aocl` to do a bunch of miscellaneous tasks
# Drivers, Libraries, and Files
An AOCL installation included the following in `ALTERAOCLSDKROOT`. Note that this is a good reference for [[opencl]] to see what a practical 'platform' looks like.

`host/include`
- OpenCL 1.0 header files required to link the host application
`host/<OS>/lib`
- OpenCL runtime and platform API implementations
# Altera Offline Compiler
According to [[zohouri-2016]], the **Altera Offline Compiler** `aoc` included:
- A [[high-level-synthesis]] tool to compile OpenCL C into Verilog
- An [[opencl]] runtime to enable the use of FPGAs as openCL devices
Despite the baked-in parallelism of openCL's work-item/work-group abstraction, `aoc` uses single-item work kernels as the preferred execution model.

Since RTL synthesis takes hours, compilation occurs *offline*. In 2016, SPIR-V had just come out so the compiler did not support it as the intermediate language. Instead, like most openCL compilers at the time, it operated on [[llvm|LLVM IR]]. The final compilation output of the altera openCL compiler is an FPGA bitstream in the *Altera Offline Compiler Executable file* (`.aocx`) format.

![[Pasted image 20231125083713.png]]

# Programming the FPGA
The FPGA must be programmed with a *hardware image* #conjecture this is where the term *device image* in [[oneAPI]] comes from. This image contains kernel code, as well as various logic required by the OpenCL runtime, board interfaces, etc. The `aocl flash` utility can be used to program the `aocx`  onto the FPGA.

Each board has some precompiled hardware interfaces that `aoc` 'links' together with the kernel to interface with the openCL runtime. This is mostly provided by the [[board-support-package]] (BSP), but also includes things like PCIe blocks, memory controllers, clock generators, etc.

![[Pasted image 20231125093251.png]]
Each kernel is compiled to an openCL compute unit.
# References
[[zohouri-2016]]
[2014 AOCL Getting Started Guide](https://www.intel.com/content/dam/www/programmable/us/en/pdfs/literature/hb/opencl-sdk/archives/aocl-getting-started-14.1.pdf)