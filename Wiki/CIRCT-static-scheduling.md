[Official Doc](https://circt.llvm.org/docs/Scheduling/)

The scheduling of IR is formulated as an [[integer-linear-program]]. Each instruction $i$ must be assigned a starting cycle $s_i$, with the constraint that an instruction can start only once its operands have been computed. The optimization goal is to minimize the overall latency; i.e. minimize $\text{max}_{i}(s_i + l_i)$ where instruction  $i$ has start cycle $s_i$ and latency $l_i$.
# Infrastructure
The goal of the `circt::scheduling` namespace is to provide an interface between **client** passes (those that need to schedule some bit of IR), and **algorithms** (i.e. [[integer-linear-program]] solvers). It does so through the `circt::scheduling::Problems` and `circt::scheduling::Algorithms` classes.
# Operator Type
In CIRCT, the [[integer-linear-program]] is an instance of `circt::scheduling::Problem`. The **client** creates 'operator types' which model the latency of a given operation for the target architecture. For example, a given architecture might have a latency of 1 for `arith.addi`tions, and 3 for other ops.
# Construct Problem Instance
The client selects all the ops it wants to consider as part of the problem instance, and sets their operator type.
# Solve
`Algorithms.h` provides some simple schedulers; essentially they take in a problem instance and modify it to add the `startTime` property to each node.