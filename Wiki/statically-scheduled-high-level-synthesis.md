#compilers 

The classical approach to [[high-level-synthesis]], according to [[borup-2022]], is statically scheduled HLS. This involves compiling the kernel into a datapath using some number of functional units, along with some control logic known as the *Finite State-Machine* controller. This model is called the *Finite State-Machine + Datapath*, or **FSMD** model.

Statically scheduled HLS achieves speed through parallelism. Structural (or spatial) parallelism comes from using more functional units in parallel. Temporal parallelism comes from keeping those functional units busy. This can be achieved through [[hls-pipelining]].

For a concrete example, see how [[CIRCT]] does this: [[CIRCT-static-scheduling]]