## Question
Why do the clean abstraction boundaries that work well in digital design fundamentally break down in analog circuits? How does this affect EDA tool design?

## The High-Abstraction-Tolerance Success Story

**Clean Separation of Concerns:**
- Logic synthesis → placement → routing → timing closure
- Each stage operates on well-defined interfaces
- Enough noise margin to ignore most physics
- Standard cells provide predictable building blocks
- Layout of module A rarely affects electrical behavior of module B

**Why This Works:**
- Regenerative behavior creates large noise margins
- Can abstract away continuous voltage variations
- Process variations don't break discrete functionality
- Routing is primarily about connectivity, not precise electrical behavior
- **Key insight**: These aren't "digital" properties - they're properties of circuits with high abstraction tolerance

## The Low-Abstraction-Tolerance Reality

**Cross-Cutting Dependencies:**
From KOAN (1991): Expert analog layout involves "shaping, folding, placing, and merging individual devices" where "many connections are achieved by abutment rather than explicit wires, and some fraction of the remaining wires is routed directly over devices."

**Why Clean Boundaries Fail:**

1. **Geometry = Electrical Behavior**
   - Device matching requires global layout awareness
   - Parasitic coupling between distant elements
   - Dummy device placement affects local field patterns
   - Process gradients require compensation at layout level

2. **Process-Dependent Optimization**
   - Cannot separate "logic" from "implementation"
   - Device sizing depends on process parameters from the start
   - Matching strategies vary by process node
   - No stable intermediate representations for "partial compilation"

3. **Multi-Objective Optimization with Coupled Variables**
   - Area, parasitics, matching, thermal effects are intertwined
   - Optimizing one aspect affects all others
   - Cannot decompose into independent subproblems

## Implications for EDA Tool Design

**The Macrocell Dilemma:**
- Digital-style macrocell approach (device generation → placement → routing) loses critical optimizations
- But monolithic approaches don't scale to complex circuits
- **Open question**: How to achieve both scalability AND preservation of analog-specific optimizations?

**Intermediate Representation Challenge:**
- Digital compilers can maintain process-agnostic IRs until late stages
- Analog requires process awareness throughout the flow
- **Question**: What would process-aware IRs look like? How would retargeting work?

**The Abstraction vs Performance Tradeoff:**
- MAGICAL (2019) chose macrocell despite citing KOAN's critique
- Possible that ML techniques can recover some lost optimizations
- But fundamental question remains: Can any abstraction preserve the cross-cutting nature of analog optimization?

## Related Questions
- [[What Makes Analog EDA Different From Digital EDA]]
- [[The layout problem]]
- [[How Is The Layout Problem Formalized]]

---
*Part of [[MicroAlchemy - EDA Development Questions]]*