In 1978, Intel introduced the [[8086]] processor.

In 1985, Intel introduced the 80386, which was 32 bits. It was around this time that the term x86 became common, which is why its synonymous with 32-bit compatibility. This processor was later rebranded `i386` (or just `386`).

By 2004, Intel had a 64 bit architecture. In 1999, AMD began work on another extension to the x86 architecture; this time to 64 bits. Internally, they referred to it as x86-64, and later as AMD64. Intel eventually adopted these extensions under the name IA-32e.

In 2023, Intel announced that they are looking into removing legacy support to create a simplified architecture known as x86S. Because of all the backward compatibility, all x64 CPUs boot into the same state ([[x86-real-mode]]) as the original 8086 processor! Bootloaders have a lot code that just bootstraps into the 64 bit mode actually used by a modern operating system.

There are three address spaces in x86. 
- logical
	- segment + offset
- linear
	- full 32 bit address
	- linear because they are all unique (unlike logical ones which can overlap because of 8086 segmentation)
- physical
	- The actual signal sent on the address pins of the CPU
Logical addresses are produced by programs using the `ss:of` syntax, and are turned into linear addresses by the segmentation unit on the CPU. These are then turned into physical addresses by means of the *paging unit*.



Understanding the Linux Kernel
[x86S Proposal](https://www.intel.com/content/www/us/en/developer/articles/technical/envisioning-future-simplified-architecture.html)
https://www.cs.umd.edu/users/meesh/cmsc411/website/projects/blunck/x86.html