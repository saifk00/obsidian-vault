#digital-hardware #compilers 
# Motivation
The history of software is a history of increasing levels of abstraction. From punch-hole cards to python, the industry has greatly benefited from leveraging layers of abstraction and interfaces between them (e.g. ABIs to operating systems) to build complex systems quickly. In the realm of hardware, however, things are different. RTL is still the dominant way to design hardware and [[system-verilog]], the most advanced of the RTL languages, is sorely lacking powerful abstractions (e.g. metaprogramming). The problem is compounded by the fact that [[moores-law]] implies that hardware complexity is ever increasing, so designing it can quickly become infeasible. The problem, according to [[borup-2022]] is that hardware interfaces are highly latency-sensitive and device-specific.

High level synthesis, or HLS, is about transforming a software program into hardware that is *semantically equivalent*, but more efficient in some sense (chiefly through leveraging spatial/temporal parallelism).

# Concepts
- There are two approaches to HLS; they are not mutually exclusive - there has been research on combining the two for the best of both worlds:
	- [[statically-scheduled-high-level-synthesis]]
	- [[dynamically-scheduled-high-level-synthesis]]
- According to [[borup-2022]], there is a need for [[domain-specific-hls]]