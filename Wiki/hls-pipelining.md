in [[high-level-synthesis]], we can achieve higher kernel performance by maximizing the temporal use of allocated hardware resources. This comes in two flavors:
1. Inter-kernel: ([[hls-loop-pipelining]])
2. Across kernel invocations: ([[hls-task-pipelining]])

The main barrier to pipelining is the presence of [[digital-hardware-hazards]].  Since the hardware is *statically* scheduled, we must assume the *worst case* for hazards. For example, if we had the following kernel:
```c++
void incrementHistogram(vec<int> H, vec<int> F) {
	for (ind : F) {
		H[ind]++;
	}
}
```

We dont know if the indexes into `H` repeat - if they do, we have a `RAW` hazard. Assuming loads/stores take 1 cycle and adds take 3 cycles, we would have to do the following:
```
0          1             2     5              6
| load ind | load H[ind] | add | store H[ind] |
| ---------------------------- | load ind     | load H[ind] | add |store H[ind]|
```
Note that we can overlap the store of iteration 1 with the load of iteration 2 since the dependency is only from the `store H[ind]` of one iteration to the `load H[ind]` of the next.

This limits the [[hls-initiation-interval]] of this loop to 5.