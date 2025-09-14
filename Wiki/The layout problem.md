The guiding questions
- how is the layout problem formalized in the literature?
- Has anyone applied the principle of stationary action to come up with a smooth differentiable function for layout in the phase space that incorporates constraints?
- What are the standard techniques to the general layout problem?

[ANAGRAM](link-needed) (1988) - Precursor using simulated annealing for macrocell layout → [[Simulated Annealing in EDA History]]

[KOAN/ANAGRAM II](https://ieeexplore.ieee.org/document/75012) (1991)
- "Macrocell style"
	- "In this style, **parameterized module generators** produce geometry for individual devices, a **placer** arranges these devices, and a **router** embeds the wiring"
	- They posit that this is done to mimic digital design flows, and that it is _fundamentally the wrong approach_ when applied to analog design.
		- **Core problem**: Digital abstractions like slicing-style placement, channel routing, and area minimization "actually interfere with the type of low-level optimizations common in manual analog cell layout"
		- **What gets lost**: Device shaping/folding, abutment connections, over-device routing, parasitic-aware optimization
		- **Why it matters**: These techniques reduce both area AND device parasitics - the optimization objectives are intertwined, not separable
	- **KOAN's solution**: Still macrocell, but with special leniences/exceptions for analog-specific needs
		- **Critical insight**: They worked around the limitations rather than fundamentally rethinking the approach
		- **Question**: What if we embraced analog complexity instead of trying to force it into digital-inspired abstractions?
[MAGICAL](https://ieeexplore.ieee.org/document/8942060) (2019)
- Part of [[DARPA IDEA]]
- **Contradiction**: Still uses macrocell style despite citing KOAN
- Layout = {placement, routing, constraint handling, design space pruning}
- **Why the contradiction?**: Possible explanations:
	- ML techniques might overcome KOAN's fundamental objections
	- Different problem scope (circuit-level vs device-level optimization)
	- Computational tractability vs optimality tradeoff
	- **Question**: Did MAGICAL actually address KOAN's abstraction critique?
- Main contribution - humans shouldnt have to provide very detailed constraints (automate some constraint extraction)
- Pain point surfaced - existing IC layout tools have 'poor accessibility'
	- [[What Makes Analog IC Layout Tools Inaccessible]]?
- Verified with 'industrial standard verification tools'
- Input: circuit netlist + design rules
- Modules:
	- Parameterized device generator
		- Design elements that respect the PDK rules (aka 'design rules'). We will need to respect design rules at _every step of the flow_ so our final layout is valid by construction.
	- Constraint extraction
		- Constraints = {symmetry, design-rules(PDK), }
	- Placement (analytical framework from [24])
		- WellGAN - DNN for well generation. This is one example of the kind of experimentation we want to enable in a more holistic framework.
	- Routing
		- hard limit on global-routing; 200x200xNlayers. That seems pretty low.
- They dont parallelize this algorithm, probably because they didnt know how.
- Why an LLVM style contribution would help these guys:
	- "Lack of training data has been a major challenge in machine learning based EDA algorithm"
	- "the lack of a unified test circuit benchmark suite makes it difficult to evaluate and compare different AMS EDA tools"
https://dl.acm.org/doi/pdf/10.1145/3299902.3309751
## History
As always, history is our guiding star. → See [[Historical Evolution of IC Layout Tools]] for comprehensive timeline research.

Early endeavors for automated IC layout:
- Simulated annealing
	- [ ] Todo, look into the timeline of simulated annealing and figure out why it was popular
- **Historical Questions to Answer:**
	- What were the very first automated layout tools?
	- When did macrocell paradigm actually emerge?
	- What tools was KOAN specifically critiquing in 1991?
	- How did analog/digital tool development diverge?