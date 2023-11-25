[Khronos OpenCL 3.0 Spec](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_API.html)
[Guide](https://github.com/KhronosGroup/OpenCL-Guide)
# Overview
Whether or not [[moores-law]] is dead, the reality is that the industry has fully embraced a heterogenous computing ecosystem that involves things like GPUs, DSPs, and other [[hardware-accelerator]]s. These accelerators are very different from traditional [[von-neumann]] CPU architectures. They have complex memory hierarchies (unlike CPUs where there is a global address space assumed by a process), and have all sorts of device specific ops.

The **Open Compute Language** specification - OpenCL for short - was developed to unify different device models into a single low-level API that can form the foundation layer for a fully heterogenous computing ecosystem. As a low-level API, it provides as much explicit control over kernel execution, memory allocation, and host-device synchronization as possible. 

See [[altera-opencl]] for a practical OpenCL platform. Pay particular attention to what they needed to do to support OpenCL 1.2, and how that may have affected the evolution of OpenCL itself.
# History
Initially developed by Apple, the OpenCL 1.0 spec was released on 2008-12-08 by the [[khronos]] heterogenous compute working group (Apple, AMD, IBM, Qualcomm, Intel, Nvidia). The latest version is OpenCL 3.0 which was released 2020-09-30.
# Structure
The [OpenCL framework](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_API.html#opencl-framework) consists of two APIs, and a compiler for kernels.
## APIs
The [[openCL-API]] enables the coordination of parallel computation across heterogenous processors. It also enables the management of a heterogenous system through things like device discovery, initialization, etc. Correspondingly, the API is itself divided into two parts:
- A **runtime** API
	- Compilation of kernels for specific devices
	- Loading of kernels and arguments into devices
	- Gathering results from devices
- A **platform** API
	- Discovering devices
	- Setting up devices
## Kernel Programming Language
In addition to an API for using/managing devices, OpenCL must provide some way for users to write kernels which are executed on devices. There is a bit of a complicated history - see [[opencl-spirv-llvm-history]] for details. Suffice it to say that kernels may be written in any language that has a [[SPIR-V]] backend: that includes but is not limited to [[SYCL]], OpenCL C, OpenCL C++, and C++ for OpenCL.




