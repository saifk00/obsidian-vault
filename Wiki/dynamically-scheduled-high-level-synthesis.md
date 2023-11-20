#compilers 

One approach to [[high-level-synthesis]] is dynamically scheduled HLS. In contrast to [[statically-scheduled-high-level-synthesis]], dynamically scheduled HLS is able to minimize the [[hls-initiation-interval]] with respect to [[digital-hardware-hazards]] by detecting them at runtime.

Dynamic scheduling is based on the theory of [[hls-elastic-circuits]].

See [[CIRCT-hls-dataflow-lowering]] for details on how this can be achieved.