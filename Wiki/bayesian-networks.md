#statistics

A [[bayesian-probability|Bayesian]] Network is one type of [[probabilistic-graphical-model]]. It represents a situation as a [[directed-acyclic-graph]] where nodes are [[random-variables]] and edges represent [[statistical-conditional-dependence| conditional dependencies]].

Bayesian networks are useful for modelling situations where we measure some *outcome*, and want to reason backwards to one of several *causes* of that outcome. For example:
- Given some symptoms, find the likelihood that the patient has a specific disease
- Given a speech signal, find the likelihood that the sound was one of several [[phoneme]]s