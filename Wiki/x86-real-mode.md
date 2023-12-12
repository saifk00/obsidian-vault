> **Real mode**, also called **real address mode**, is an operating mode of all [x86](https://www.wikiwand.com/en/X86 "X86")-compatible [CPUs](https://www.wikiwand.com/en/Central_processing_unit "Central processing unit"). The mode gets its name from the fact that addresses in real mode always correspond to real locations in memory


After POST, the motherboard sends a `RESET` signal to the CPU, which sets a few registers to a known state:
- `cs` - the code segment register
- `eip` - the instruction pointer
which begins to fetch instructions at phsyical address `0xfffffff0` (32 bit addr)
# Bibliography
Understanding the Linux Kernel, Appendix A
https://wiki.osdev.org/Real_Mode
https://www.wikiwand.com/en/Real_mode