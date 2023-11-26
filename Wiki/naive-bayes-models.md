# Naive Bayes Models
Naive Bayes models are a class of bayesian networks where we assume that some set of observed features ${X_0, X_1, ... X_n}$ are aspects of some class $C$, and that they are all conditionally independent given the class $C$. For example, in the classic [[student-bayesian-network]], the class is the student's intelligence $I$ and the observed variables are the grade and SAT score.

It is often used when the goal is to determine, based on the observed features, what class the evidence belongs to. These types of models were often used for medical diagnosis because of their *simplicity*, however it was found that (especially as the number of features increased), the accuracy of these models failed because of their strong assumptions about the independence of features from eachother. In particular, it tended to 'overcount' evidence from correlated features (e.g. if the features were symptoms, high blood pressure and obesity are highly correlated, and this model would overestimate the influence of one of these symptoms when determining the disease).

# References
[[koller-2009]] sec. 3.2