https://www2.eecs.berkeley.edu/Pubs/TechRpts/2016/EECS-2016-9.pdf
# Overview
FIRRTL was developed to provide an IR for [[chisel]] after all metaprogramming was removed.

The authors identify a few core shortcomings of the old design of[[chisel]] that prevented adoption in industry. Most can be grouped under lack of understanding - hardware designers simply aren't well versed in Scala, Functional programming, etc. but a more interesting one is that the generated Verilog is unreadable and slow to simulate, and that it was difficult to target Chisel from other languages due to lack of specifications.

To follow good compiler design practices, the authors propose [[FIRRTL]] , an intermediate representation for RTL that, in [[chisel]], is produced right after elaboration. It has first-class support for some things that might seem quite high level for an HDL - vectors, bundles, conditionals, etc.

FIRRTL is then progressively lowered to LoFIRRTL - essentially a netlist which can easily be translated into Verilog.

Using FIRRTL, the host language (e.g. Scala for [[chisel]]) is used only for its metaprogramming facilities (i.e. for generating complex hardware using software practices), so additional frontends (e.g. in C++) can be created while reusing the majority of the optimizations and lowering transforms provided by the FIRRTL community.

The rest of the paper is a specification of FIRRTL.
# Connects
FIRRTL has a notion of **gender** for expressions; female for receiver, male for transmitter, and bi-gender for both ways.
# Observations
- FIRRTL is *implemented* by the LLVM subproject [[CIRCT]]