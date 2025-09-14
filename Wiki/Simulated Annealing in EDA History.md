## Question
What role did simulated annealing play in early EDA development, and why was it so popular for layout optimization in the 1980s?

## Historical Development of Simulated Annealing

**Origins (1983):**
- Developed by Kirkpatrick, Gelatt, and Vecchi at IBM
- Inspired by the physical annealing process in metallurgy
- Statistical mechanics approach to optimization

**Why It Emerged in the 1980s:**
- Computational power finally sufficient for iterative optimization
- Need for global optimization in complex combinatorial problems
- Layout problems are inherently discrete, non-convex optimization challenges

## Application to IC Layout (1980s)

**ANAGRAM (1988)** - First major application:
- Macrocell-based layout using simulated annealing for placement
- Preceded KOAN/ANAGRAM II (1991) which critiqued the macrocell approach
- Demonstrated that SA could handle large solution spaces in layout

**Why Simulated Annealing for Layout:**
- **Discrete optimization**: Layout involves discrete placement decisions
- **Multiple objectives**: Area, wirelength, timing - SA handles multi-objective naturally
- **Constraint handling**: Can incorporate complex geometric and electrical constraints
- **Escape local minima**: Critical for layout where greedy algorithms get trapped

## Technical Characteristics in EDA Context

**Algorithm Properties:**
- Probabilistic acceptance of worse solutions (controlled by "temperature")
- Gradual cooling schedule allows convergence to global optimum
- Naturally handles discrete moves (device swaps, rotations, mirroring)

**Layout-Specific Adaptations:**
- Move sets: swap adjacent devices, rotate, mirror, small translations
- Cost functions: weighted combination of area, wirelength, constraint violations
- Cooling schedules: tuned for layout convergence properties

## Why It Lost Favor

**Computational limitations:**
- Extremely slow convergence for large problems
- Poor scalability with increasing circuit complexity
- No parallelization strategy in early implementations

**Algorithm limitations:**
- Difficult to incorporate hierarchical design constraints
- Hard to guarantee timing closure
- Limited ability to handle modern multi-objective optimization needs

## Legacy and Modern Relevance

**Historical impact:**
- Established optimization-based approaches to layout
- Demonstrated feasibility of automated placement for complex circuits
- Influenced development of later metaheuristics (genetic algorithms, particle swarm)

**Modern context:**
- Largely superseded by gradient-based methods and ML approaches
- Still used in specialized applications requiring global optimization
- **MAGICAL connection**: Modern ML approaches attempt to capture the global optimization benefits of SA with better computational properties

## Connection to ANAGRAM → KOAN Evolution

**ANAGRAM (1988)**: "Simulated annealing works for macrocell layout"
**KOAN/ANAGRAM II (1991)**: "But macrocell itself is fundamentally limited for analog"

This progression shows the evolution from **algorithmic innovation** (better optimization) to **architectural critique** (wrong abstraction boundaries).

## Related Questions
- [[The layout problem]] - ANAGRAM as precursor to KOAN
- [[Historical Evolution of IC Layout Tools]] - SA as part of 1980s automation wave
- How do modern ML approaches in [[MAGICAL]] compare to SA's global optimization properties?

---
*Part of [[MicroAlchemy - EDA Development Questions]]*