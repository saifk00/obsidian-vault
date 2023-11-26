[Specification](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_API.html)

# [Architecture](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_API.html#_the_opencl_architecture)
## Platform Model
The hierarchy is this:
- Host
	- Device
		- Compute Unit
			- Processing element
A device has a lot of flexibility as to how it maps computation onto processing elements. There are two broad categories of computation - if all the PEs in a CU execute the same sequence of statements, the control flow is called *converged*, otherwise it is *diverged*.

An OpenCL **platform** must provide a compiler to translate programs written in [[opencl-c]], [[SPIR-V]], or other implementation-defined binary objects into executable objects. The compiler may be *online* or *offline*. The openCL API provides a function for using the online compiler, while offline compilation is platform-specific. The runtime API provides a method to load and execute previously compiled device programs.

There are two **platform profiles**: *full* profiles must provide online compilers for all devices, while *embedded* platforms are not required to do so.

## Execution Model
There are two distinct units of execution in the openCL execution model. There is a **host program** that executes **kernels** which execute on one or more devices on the platform.

Host programs may create command queues to interact with a device. The command queue is used to enqueue kernel execution, transfer/map memory, and synchronize. There are also device-side command queues that can be used by kernels to create *child kernels* (e.g. built-in kernels).

A kernel together with its arguments and **index space** form a *kernel instance*. When executing on a device, the kernel instance executes for each point in the index space. Each of these point-executions is called a *work item*. The device manages work items in groups called *work groups* and *work sub-groups* by dividing the index space into coarser grained chunks.

The *index space* is also called an [[NDRange]] for "N-dimensional range". N is one, two, or three. #conjecture this is because of GPUs. For each dimension, we specify the following three values:
1. The length of the index space in that dimension
2. The offset F indicating the initial value of the index in that dimension
3. The size of a work-group in that dimension

## Memory Model
There are two fundamental memory regions: host and device. Device memory consists of the following *address spaces*:
1. Global memory
	- Shared by all work items in a context (potentially separate work groups and even devices). All work items have read/write access to global memory.
2. Constant memory
	- A region of global memory that is constant during execution of a kernel instance
3. Local memory
	- A region of memory shared by a work-group
4. Private memory
	- A region of memory private to a work-item
Note that local and private memories are always private to a device, while global and constant memories are shared by all the devices in an OpenCL context.

All four address spaces belong to a single, shared *generic address space* to allow functions to modify pointers in global, local, or private memories. The generic address space (GAS) has the following properties:
- A pointer to GAS can be cast to global,local,private
- A pointer to global,local,private can be cast to GAS
- A pointer to global,local,private can implicitly convert to a GAS pointer
- A GAS pointer **cannot** implicitly convert to global,local,private

Addresses pointing into global memory are *not* consistent across devices and kernel instances. It is more like a pool of objects than an actual address space. 

- [ ] There exists [[opencl-shared-virtual-memory]] which allows a proper global address space.

Global memory holds objects of type `cl_mem` which is one of the following:
1. Buffer - a contiguous array with random access
2. Image - 1,2,or 3D image based on one of the standard formats in graphics
3. Pipe - an ordered sequence of data. used for [[producer-consumer]] kernels to communicate