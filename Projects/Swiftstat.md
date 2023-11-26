# Theory
- The core of swiftstat is the theory of [[probabilistic-graphical-model]]s
	- Currently, it only implements [[bayesian-networks]]
# Principles
- **Example Models**: We are primarily interested in models that are in some sense 'time-sensitive'. The goal here is to *accelerate* inference. For example, things like medical diagnosis, while important, are probably not as time sensitive as speech signal processing. It is already widely accepted that medical diagnosis can take a few weeks.
	- Good candidates
		- Anything with real-time data
			- Speech recognition
			- Live medical diagnostics (emergency alerts for people in ER)
		- Anything with massive amounts of data

# TODOs
- [ ] I think I misunderstood [[gibbs-sampling]] in our original implementation. Fix our implementation for accuracy
	1. We need to be sampling from a node conditioned on its *markov blanket*, not just the parents. Children should pass their values up to the parent
- [ ] Rethink the `Sample` class - its just an alias around a `UInt` but adds some complexity since it seems like some users need to use `.sample` and some dont.
