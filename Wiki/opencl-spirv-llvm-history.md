There is a bit of a complicated [[the-history-of-a-subject-and-prevailing-ideology-are-intertwined|history]] here so there are actually quite a few ways to write an OpenCL kernel. This section is an attempt to wrangle that history so that various developments make sense.
### OpenCL 1.0 (2008): OpenCL C
In the original OpenCL 1.0 specification, the only way to program a kernel was using the **OpenCL C** language. This was a subset of C99 with some extensions for expressing parallelism. OpenCL implementations were required by the standard to provide a compiler that produced kernels from OpenCL C.

### OpenCL 1.2 (2012): SPIR
But building a compiler is hard work. To implement OpenCL as rapidly as possible, vendors (Intel, AMD, Nvidia) decided to base their OpenCL C compilers on [[llvm]]. By 2012 [[llvm|LLVM IR]] had become [***"the de factor OpenCL IR"***](https://www.phoronix.com/news/MTE4MzM). Interestingly, this is the same year that LLVM won the ACM software system award.

To reduce this duplication of efforts, a Khronos working group with contributors from Intel, ARM, AMD, Apple, Nvidia, Qualcomm (and interestingly Codeplay) developed the **Standard Portable IR** or SPIR 1.0 specification. Here's a quote from its introduction:

> [!quote]
> The goal of SPIR is to provide a portable interchange format for partly compiled OpenCL C programs. The format is vendor neutral, not C source code, and designed to be efficiently loaded by an OpenCL implementation. \[...\] It is designed to be useful as a target format for compilers of programming languages **other than OpenCL C**. This is a secondary goal of SPIR
>  

That is, SPIR was initially just meant to allow OpenCL frontends to be developed independently from backends.

The natural question arises - if LLVM was the de-facto IR for OpenCL vendors, why did Khronos group create a whole new IL (SPIR) instead of just adopting LLVM? The answer is that LLVM IR is *not standardized or backwards compatible* ([[llvm-weak-compatibility]]) something that is unacceptable for drivers! See https://www.neilhenning.dev/wp-content/uploads/2015/04/WhySPIR-V-Notes.pdf for details.

### OpenCL 2.1 (2015): SPIR-V
At the same time, the Khronos group was developing [[vulkan]] to supercede [[opengl]]. Again, to avoid reduplication of effort, they first released [[SPIR-V]] to act as the common IR of [[vulkan]] and [[opencl]] - note that Vulkan would not be released until 2016. This offloaded the work of writing a front-end compiler from the drivers meaning that vendors like Nvidia and AMD had to do less work. SPIR-V was no longer based on LLVM IR since the latter was never meant to express heavy parallelism, thus the [[spirv-llvm-translator]] was developed.

Here's a [quote](https://github.com/KhronosGroup/OpenCL-Guide/blob/main/chapters/programming_opencl_kernels.md) from the Khronos OpenCL guide:
>[!quote]
>*Early OpenCL implementations used proprietary binary formats for offline compilation by a device driver and were thus not portable to other devices. To resolve this, [[khronos]] developed [[SPIR-V]] as the offline compilation target*

This allowed the industry to develop new frontends for OpenCL that didn't necessarily go through OpenCL C. For example, [[SYCL]] was born around this time and initially targeted SPIR as a backend. [[halide-lang]] is another example of how [[domain-specific-languages]] are enabled by OpenCL using SPIR-V as a backend.

### OpenCL 2.2 (2017): OpenCL C++
On 2017-05-16 the OpenCL 2.2 specification was released. It introduced the **OpenCL C++** kernel language to the specification. [[SPIR-V]] became the official intermediate language for offline compilation - it serves as the input to a `clCreateProgramWithIL` call.

### OpenCL 3.0 (2020): C++ for OpenCL
Yes - confusing name. C++ for OpenCL is a community-led effort to enable writing OpenCL kernels in C++ *without restriction* (OpenCL C++ is a *subset* of C++). The OpenCL C++ kernel language is deprecated as of this release.

- [ ] https://www.khronos.org/openvx/



- apple objective c first commercial llvm project
- confirmed jeff 2012 is the inflection point
- mlir inflection point now
- 