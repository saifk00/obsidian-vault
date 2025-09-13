A software compiler transforms general purpose code to assembly. A *hardware compiler* transforms general RTL to specialized RTL. [[CIRCT]] is one such compiler that operates on RTL represented by [[FIRRTL]].

In my opinion, we are at a turning point in hardware compilers. It currently takes hours (maybe days) to produce a bitstream (synth, place and route, timing, etc.) from source code. Furthermore, source code is *not reusable* as it is tightly coupled to the underlying hardware library. There is a (correct for now) belief that this allows for optimizations that are not possible to do in a hardware-agnostic manner.

This is analogous to the days in which compilers for *software* were slow, and source code was written for a particular assembly format.

The big picture here is that hardware enabled compilers, which enabled software to amortize its NRE costs over all the *uses* of developed code (each time a function is reused, its cost per use decreases). This enabled further investment in software, which in turn created the demand for better hardware. The gameplay loop was set, and Moore's law came in. Since 1972, hardware doubles in speed for the same price, enabling further investment in software which will automatically get faster over time. But Moore's law is about to hit a wall. At the same time, we have hit this turning point in compilers. If we can use this to our advantage, if we can use software to design the next generation of hardware in a faster and cheaper way, relying on the amortization of high level synthesis over all the specialized hardware that uses it, we can usher in a new age of growth for the industries.

# References
[[izraelevitz-2019]] Ch.4