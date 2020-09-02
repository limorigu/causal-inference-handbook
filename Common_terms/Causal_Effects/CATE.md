Motivation
====

The [ATE](Common_terms/Causal_Effects/ATE.md) is sometimes not enough to calculate a causal effect to answer a question of interest. For example, if we ask the question: "Does this new cancer drug work better for women, than for men?", the average treatment effect will not be helpful. Instead, we need a treatment effect on a specific group of interest, for example, the causal effect on women vs. the causal effect on men. The Conditional Average Treatment Effect (CATE) can help us estimate causal effects to answer group specific questions. We are still looking at an average treatment effect in the sense of looking at an expectation across a variable, but we now also condition on an additional covariate of interest, such as gender.

Definition
====
> Given three random variables X, Y and Z, where X is binary,
> CATE = E[Y|do(X=1), Z=z] - E[Y|do(X=0), Z=z]

Thus, CATE is very closely related to ATE, but now also conditions on the value of a specific covariate of interest, which helps us answer causal queries about the effects of a treatment on average *within a specific group*, determined by covariate Z. 

In a similar way to the ATE, CATE can also be extended to continuous or categorical treatments by fixing two levels of interventions on the random variable X, x_1 and x_2:

> CATE = E[Y|do(X=x_1), Z=z] - E[Y|do(X=x_2), Z=z]

Once again, note that this setting usually requires some definition of treatment of interest, x_1, against some baseline treatment level, x_2, based on the specific use case. To continue with the medical treatment running example, we might want to consider x_1 and x_2 to be two different doses of the drug of interest.

Intuition
====
As stated above, if we would like to know the average treatment effect of a drug on recovery *within a subgroup of a population*, such as females, we would need to estimate the following CATE:

> E[Recovery|do(Drug_taken=1), G=Female] - E[Recovery|do(Drug_taken=0), Gender=Female]

Further Reading
====
For more, see:
1. [Meta-learners for Estimating Heterogeneous
Treatment Effects using Machine Learning](https://arxiv.org/pdf/1706.03461.pdf)
2. [Estimating Conditional Average Treatment Effects](http://www.personal.ceu.hu/staff/Robert_Lieli/cate.pdf)
3. [Jonathan Mummolo's slides on Treatment Effect Heterogeneity and Multiplicative Interaction Models](https://scholar.princeton.edu/sites/default/files/jmummolo/files/interaction_models_jm.pdf)