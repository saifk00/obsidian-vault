Traditional HLS compilers like [[intel-hls]] are based on imperative languages like C/C++. This forces users to lower their domain abstractions (e.g. tensors for ML) into C++ constructs, which may result in missed opportunities to perform optimizations on the higher level constructs.

There are tools that are specifically designed for generating FPGA based binarized neural networks (FINN), which are able to perform optimizations on the higher level concept of tensors that traditional C++ based HLS tools cannot (since the user is forced to lower these abstractions to C++).
-  This sounds like a job for [[MLIR]]
- The back-end equivalent of this problem is addressed by [[FIRRTL]]

