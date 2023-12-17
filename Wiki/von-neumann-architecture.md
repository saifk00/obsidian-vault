The Von Neumann architecture refers to the original design of the EDVAC as laid out by Von Neumann in his 'First Draft on the Design of the EDVAC'.

It is important to remember that the term 'architecture' had not been applied to computing until the '60s: [[origins-of-the-architectural-metaphor-in-computing]]
# First Draft on the EDVAC
https://people.csail.mit.edu/brooks/idocs/VonNeumann_EDVAC.pdf

## 4. Computing Elements
Section 4 of [[von-neumann]]'s report is quite potent. In it, he abstracts the fundamentals of a computing 'element' from what we would now assume are electrical transistors:

> Every digital computing device contains certain relay like *elements* with discrete equilibria. Such an element has two or more distinct states in which it can exist indefinitely ... The relay action manifests itself in the omission of stimuli by the element whenever it has itself received a stimulus of the type indicated above. The emitted stimuli must be of the same kind as the recieved one, that is, they must be able to stimulate other elements.

In fact, this was written *before* the invention of the transistor! At the time, it was vacuum tubes, wheels, telegraph relays, etc.

In fact, in keeping with the [[cybernetics|cybernetic]] disposition of [[cold-war-military-research-projects]], [[von-neumann]] introduces computing elements as an analogue of the neuron.

# Key Points
In the article [[myth-of-the-harvard-architecture]], the authors identify ten aspects of the so-called "Von Neumann Architecture," meaning the computing machine described in [[von-neumann]]'s draft for the design of the [[edvac]] (the [[ENIAC]]'s successor)

1. Large addressable read/write memory
2. Binary number representation
	- The [[ENIAC]] used decimal; 10 tubes per digit, whereas the EDVAC used 4
3. Centralized storage,arithmetic,control unit
	- The [[ENIAC]] used 20 'accumulators', each with working storage for a number, plus arithmetic and control units
	- The above is not scalable with the increased memory space of the Von Neumann architecture
4. Special purpose registers
	- Instead of replicating accumulators, have small fast storage units that are *hardwired* to arithmetic/control units; e.g. the Accumulator need only be wired to memory (fetch/store) and the ALU (arith.) instead of to every possible functional unit
5. Instructions held in numbered memory locations
6. Interchangable memory
	- i.e. treat memory as a single working space, where all types of data (including instructions) can fit in any slot
7. Program loadable from external media
	- [[von-neumann]] foresaw that we would need to quickly change programs as computers got faster
8. Define a *program* as a sequence of atomic instructions
9. Automated jumps
	- Paper-tape machines required physical interaction to branch to different sequences
10. Instructions operating on variable addresses
	- "The First Draft indicated that it should be possible to vary the address part of an instruction. One need for that was to apply the same code to different data elements successively"
	- Enabled subroutines
	- "It is misleading to equate this principle with the idea of ‘selfmodifying code’, not only because of the alternative ways in which it could be implemented, but because even the initial idea did not permit instructions to overwrite other instructions – only the address portion of those instructions"