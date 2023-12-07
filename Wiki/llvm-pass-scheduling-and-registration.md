The simple IR pass pipeline model of [[llvm]] poses two problems: how can we ensure previously run analyses are valid (and if not, when to re-run them), and how can we ensure passes that are dependent on previous passes are ordered correctly?

To solve this, LLVM provides a pass declaration interface. Each pass specifies:
- Prerequisite passes
- Any analyses that it invalidates/preserves. By default, a pass invalidates *all* analyses

Passes are then registered with the [[llvm-pass-manager]] as one of the [[llvm-pass-categories]].

# References
[[izraelevitz-2019]] 4.1