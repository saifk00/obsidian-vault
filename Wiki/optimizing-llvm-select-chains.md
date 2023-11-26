# Background
I came across an issue where we wanted to optimize the following pattern in LLVM IR:
```llvm
%0 = select i1 %cond, <Ty> %a, <Ty> undef
%1 = select i1 %cond, <Ty> %0, <Ty> %c
```
since `%0` and `%1` share the condition, this could be simplified to
```llvm
%1 = select i1 %cond <Ty> %a, <Ty> %c
```
# Optimization
Pseudocode for performing the optimization is as follows
```python
# assumes I1 feeds into I2
def optimize(I1, I2):
	if I2.TrueValue == I1.Value:
		I2.TrueValue = I1.TrueValue
	else
		I2.FalseValue = I1.FalseValue
	# rely on dead code elimination to get rid of I1
```
# Solution
The obvious `O(N^2)` solution is to check all pairs of select statements, and perform the optimization if (1) the conditions are the same and (2) the output of the first instruction feeds into one of the inputs of the second instruction.

But, i re-framed this problem as a graph algorithm and realized that we essentially have a topologically ordered DAG (since LLVM IR is SSA, and values are defined before they are used) where we need to perform some operation for each edge. An edge exists in this graph if
```python
	I1.Cond == I2.Cond and I1.Value in {I2.TrueValue, I2.FalseValue}
```

So I came up with the following algorithm, which is `O(N)` in the number of select statements
```python
# optimizes all the select statement chains in a basic block
# assumes I is an ordered list of all the instructions in the BB
def optimize_select_statements(I: [Instruction]):
	# only look at all the select instructions
	I = I.filter(SelectInst)
	# maps conditions to the set of values predicated on the condition
	mem = Map[llvm::Value, Set[llvm::Value]]
	for S in I:
		if S.TrueValue in mem[S.Cond] or S.FalseValue in mem[S.Cond]:
			optimize(mem[S.Cond], S)
		mem[S.Cond] += S.Value
```

Pretty neat huh? As of writing I think we won't end up using it but I was happy about this little optimization :D