An [[MLIR]] region allows hierarchical structuring of the IR. Operations may define multiple regions which each may contain a number of blocks/regions within them. The semantics of each region depends on the op itself. For example, the `scf.while` operation defines two regions: a conditional, which computes the condition, and a `body` which computes the body of the loop.