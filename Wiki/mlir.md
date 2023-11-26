A project to extend [[llvm]] for the realm of domain specific accelerators (GPUs included). Domain-specific programming models typically define their own IR/ASTs which are optimized and then lowered to LLVM. MLIR allows these models to share infrastructure by defining `dialects`, sets of operations along with validators for them. It also adds *structure* to the IR, something lost in LLVM IR which is vital for many domain accelerators.

# Textual Format
Some key differences from LLVM IR:
- Operations may have multiple results. Syntax for this is something like `%0:2 = some.op.name(%arg1, ...) : (i1, ...) -> (i32, i32)`, where the values of `%0` can be addressed like `%0#1` and `%0#2` respectively
- Operations have *attribute lists*, which may propagate arbitrary info that is known at compile time
- Operations are typed using 'functional' notation. e.g.  a function that takes two `i32`s and returns three `i8`s has the type `(i32, i32) -> (i8, i8, i8)`

# Universal Semantics
Most semantics are implemented by dialects, but there are a couple things that are universal (i.e. that come from the infrastructure itself):
1. All values are SSA
2. All values come from exactly one of
	1. An operation result
	2. A block argument

# Structure
MLIR imparts *structure* to the IR using:
1. [[mlir-block]]s
2. [[mlir-region]]s

# Dialects
- [[CIRCT]] - represents hardware circuits using a set of dialects
# Questions
- So we have this cloud of dialects and a bunch of passes (?) that can take one to the other - how do we determine the right path from IR 1 to IR 2? Does each compiler implement a specific path through the IR 'universe'? what is the philosophy here? e.g. If I want to introduce a new dialect that can ultimately be executed on the CPU, what steps to I need to take to ensure the minimal amount of lowering work done by me and the maximum amount of 'shared optimizations'?