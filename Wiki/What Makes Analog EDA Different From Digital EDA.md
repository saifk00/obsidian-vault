## Question
What makes designing an analog EDA fundamentally different from tools like KiCAD or digital flows? What are the ontological domains specific to analog design?

## The Fundamental Answer

**What makes analog fundamentally harder/different than digital?**

Digital circuits have enough noise margin to abstract away the physics. Analog circuits don't.

This simple insight explains everything else - why clean abstractions break down, why modular design fails, why each analog circuit needs custom layout, why cross-cutting optimization is required. It's all because analog circuits operate too close to the physical reality to ignore it.

## Relevant Sources and Notes
- [[high-level-synthesis]] - Digital hardware compilation approaches
- [[CIRCT]] - Digital hardware compilation infrastructure
- Need to research: Analog design constraints, verification challenges, optimization objectives
- [KOAN](https://ieeexplore.ieee.org/document/75012): "analog layout tools that merely apply known digital macrocell techniques fall far short of achieving the density and performance of handcrafted analog cells"
## Initial Investigation

### KOAN's Critique of Digital-Style Abstractions (1991)

Key quote from KOAN/ANAGRAM II:
> "Some common assumptions that help manage the complexity of large digital layouts, e.g., a slicing-style placement, the restriction that signal routing be confined to channels between placed objects, and the exclusive emphasis on minimizing wire length and area, are not essential for attacking analog device-level layout. In our experience, these assumptions actually interfere with the type of low-level optimizations common in manual analog cell layout."

**The Abstraction Breakdown:**
- **Digital assumption**: Clean separation of concerns - placement, then routing, with minimal cross-dependencies
- **Analog reality**: Cross-cutting optimizations that span traditional abstraction boundaries
  - Device shaping and folding for density
  - Abutment instead of explicit wires
  - Routing directly over devices
  - Dummy device placement for matching
  - Process-dependent optimizations

### Why Clean Interfaces Don't Work for Low-Abstraction-Tolerance Circuits

**High abstraction tolerance ("digital")**: Enough noise immunity to ignore physics
- Layout of Block A doesn't significantly affect Block B's electrical properties
- Can decompose into independent subproblems
- Standard cells with predictable interfaces
- Physics-ignoring abstractions work because of regenerative behavior

**Low abstraction tolerance ("analog")**: Must work with continuous physical reality
- Parasitic coupling between distant devices
- Matching requires global awareness of surroundings
- Process variations directly affect performance
- No "standard cell" abstraction - each design is custom to its physical context

### Intermediate Representation Problem

Unlike digital compilation where IRs can be process-agnostic until late stages, analog design is process-dependent from the start:
- Gate sizing depends on process parameters
- Device matching strategies vary by process
- Parasitic models are process-specific
- **Implication**: Hard to define stable intermediate representations for "partial compilation"

## Further Questions
- How do continuous vs. discrete domains affect design methodology?
- What role does physics simulation play in analog vs. digital verification?
- How do parasitic effects change the optimization landscape?
- Can digital compilation techniques be adapted for analog domains?

---
*Part of [[MicroAlchemy - EDA Development Questions]]*