According to [[the-mythical-man-month]], there are key differences between programs (which are easily developed by a couple of dudes in a garage), and the kind of things produced by large scale teams.

The latter are:
1. Programming _systems_: these are made of components developed by independent teams, each of which is subject to the following constraints that makes them more expensive than programs:
	- They must conform to a specification (i.e. to communicate with other components in a well-defined manner)
	- They must be *tested* against other components
	- They must conform to resource constraints (RAM, time, CPU usage, etc.)
2. Programming _products_: these are programs that can be *used and extended by others*. And as such they also face compounding constraints:
	- They must be written *generically*, which increases the input space
	- They must be tested across the whole input space
	- They must be well documented

A programming system product is the combination of the two, which Brooks estimates to be 9x more expensive than programs.

programs are more joyous to create than programs because they dont face the restrictions listed above, and are not subject to the realities of human foibles - they satisfy the purest creative urge: to build castles in the sky and realize them here on earth without a hitch.