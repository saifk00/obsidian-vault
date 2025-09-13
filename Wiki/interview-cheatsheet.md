This note just includes some common topics that I need to refresh on because they're not used much in practice but show up often in interviews.

# Heap in C++
# Parallelism
Amdahl's law
$$
S = \frac{1}{(1-P)+\frac{P}{N}}
$$
where S is the speedup, P is the fraction of the program that can be parallelized, and N is the number of parallel operations (e.g. number of CPUs)

*Make the common case fast!*
