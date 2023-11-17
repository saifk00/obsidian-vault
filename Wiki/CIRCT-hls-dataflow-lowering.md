# Overview
In [[CIRCT]], [[dynamically-scheduled-high-level-synthesis]] can be achieved based on the following dataflow operators:
![[Pasted image 20231117181455.png]]

This note goes through the method laid out in [[borup-2022]]. It is not clear to me whether this is how things are really done in [[CIRCT]] as of writing, but the principles are still important

# Maximal SSA
Recall [[variable-liveness]]. Maximal SSA ensures that all the variables that are live in an [[mlir-block]] are either (1) defined in the block, or (2) block arguments. For example, some IR like this:
```mlir
func @foo(%arg0: i32) -> i32 {
	%c = llvm.mlir.constant(42: i32) : i32
	%0 = arith.cmpi sgt, %arg0, %c : i32
	cond_br %0, ^bb1, ^bb2(%c)
^bb1:
	%1 = arith.addi %c, %c : i32
	br ^bb2(%1)
^bb2(%2: i32):
	%3 = arith.muli %arg0, %2 : i32
	return %3 : i32
}
```

See how `%arg0` is *live* during `^bb1` even though it is not used in that block (because it will be used in `^bb2` after we branch)? Maximal SSA produces this:
```mlir
func @foo(%arg0: i32) -> i32 {
	%c = llvm.mlir.constant(42: i32) : i32
	%0 = arith.cmpi sgt, %arg0, %c : i32
	cond_br %0, ^bb1(%arg0), ^bb2(%c, %arg0)
^bb1(%arg0_live: i32):
	%1 = arith.addi %c, %c : i32
	br ^bb2(%1, %arg0_live)
^bb2(%2: i32, %arg0_carried: o32):
	%3 = arith.muli %arg0_carried, %2 : i32
	return %3 : i32
}
```
# Dataflow Conversion
