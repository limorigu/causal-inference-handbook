Motivation
====
Average treatment effects, whether in the populationa at large (ATE), or subgroups in the population (CATE), are still not quantities that tell us exactly what the efficacy of a treatment would be on a specific instance in our dataset, i.e. an individual point. If we are interested in asking about the effect of a treatment on a *particular individual point*, we need another, more "zoomed in" definition, which is the Individual Treatment Effect (ITE).

Definition
====
>ITE = E[Yi|do(Xi=1), Zi=z] - E[Yi|do(Xi=0), Zi=z]

This definition follows the ATE and CATE formulations closely, but this time asks about values of outcome Y, treatment X and covariate Z as they apply to a specific, invidual datapoint of interest i. Note that by doing so, it moves from a interventional, expected outcome we can measure in RCT or via identification of causal effects, to a counterfactual definition. That is, the same individual can never both take and not take the treatment. We only get to observe one side of this ITE equation. 

We should also mention that some works define ITE as closer to CATE, see first footnote in ![Representation Learning for Treatment Effect
Estimation from Observational Data](https://papers.nips.cc/paper/7529-representation-learning-for-treatment-effect-estimation-from-observational-data.pdf).

In a similar way to the ATE and CATE, the ITE can also be extended to continuous or categorical treatments by fixing two levels of interventions on the random variable X, x_1 and x_2:

>ITE = E[Yi|do(Xi=x_1), Zi=z] - E[Yi|do(Xi=x_2), Zi=z]

Once again, note that this setting usually requires some definition of treatment of interest, x_1, against some baseline treatment level, x_2, based on the specific use case.

Intuition
====
The intuition is simple. We would like to be able to estimate the treatment effect for a specific instance, say, individual person. For example, we would understandably like to know whether a heart transplant led to recovery for a specific person, against what would have happened to that patient if they did not recieve such a transplant (see discussion in the first reference below, in the Hernan and Robin Causal Inference book, Chapter 1.1).

Further Reading
====
For more, see:
1. [Causal Inference: What If, Ch. 1.1](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/)
2. [Representation Learning for Treatment Effect
Estimation from Observational Data](https://papers.nips.cc/paper/7529-representation-learning-for-treatment-effect-estimation-from-observational-data.pdf)
3. [Estimating individual treatment effect: generalization bounds and algorithms](https://arxiv.org/abs/1606.03976)
4. [Estimating Individual Treatment Effect in Observational Data Using Random Forest Methods](https://amstat.tandfonline.com/doi/abs/10.1080/10618600.2017.1356325)
5. [Non-parametric individual treatment effect estimation for survival data with random forests](https://academic.oup.com/bioinformatics/article-abstract/36/2/629/5542949?redirectedFrom=fulltext)
