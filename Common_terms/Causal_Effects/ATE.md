Motivation
====
It is often the case that causal effect of interest can be stated as average-effect statements, when we want to ask not about the effect of a treatment on one specific instance in a dataset (which is not generally identifiable), but rather on an *on average* effect, across the dataset. Such statements are usually spelled out via the Average Treatment Effect Definition. 

Definition
====
> Given two random variables X and Y, where X is binary,
> ATE = E[Y|do(X=1)] - E[Y|do(X=0)]
To spell this out a little more, the ATE tells us what is the average causal effect, or difference between the average effect of taking a treatment (or carrying out an intevention setting the variable treatment to 1), vs. the average effect on not taking a treatment (and thus setting the variable treatment, via an intervention, to 0).

While the common formulation of ATE considers binary treatments, such as taking or not taking a drug, it can be extended to categorical or continuous treatments as well. In such cases, we could write

> ATE(x_1, x_2) = E[Y|do(X=x_2)] - E[Y|do(x_1)]
 where X is intervened at two different levels, say x_1 and x_2. Note, however, that categorical or continuous treatments ATEs require some definition of a baseline (or "control" level) to take the difference against. To continue with the medical treatment running example, we might want to consider x_1 and x_2 to be two different doses of the drug of interest.

The same definition also often appears as Average Causal Effect (for example, in Peters, Janzig and Schoelkopf's elements of causal inference, see below).

Intuition and Examples
===
This is a common query in causal inference, as it can give us a rough idea of the effect of interventions. It also follows the logic of Randomized Control Trials closely: it tells us of the difference in expectation of some outcome of interest (such as the state of a disease), in some group that has taken a treatment vs. in a *control* group, that hasn't taken the treatment (e.g. some drug under trial). 

Notice that the use of do-notation above is crucial for this RCT-like formulation: we consider the case where a randomized process led to such an intervention, assigning some individuals to a group that takes the drug, and others to the control group that doesn't take the drug. This intervention makes sure there are no lurking confounders, which might explain the presence of certain indiviuals in one of the group due to some characteristic(s) they share. For example, if the assignment to the treatment group is not random, but is associated with a higher socio-economic status, that in turn might lead some doctors to be more lenient with subscriptions of drugs, as well as affect the likelihood of recovery via other factors such as diet, excercise or stress levels -- we can no longer draw causal conclusions about the efficacy of a drug by running the usual statistical machinery on such an observed dataset!

Thus, the average treatment effect gives us a simple, crude estimate of the effect of some intervention on some outcome, and crucially does so via the do operator, and not through simple observed quantities X=0 or X=1 (or x_1, x_2 in the continuous case, etc.).

Further Reading
====
See more at:
1. [Causal Inference: What If, Ch. 1.2](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/)
2. [MIT's Economics department's summary, P. 2](https://economics.mit.edu/files/32)
3. [Elements of Causal Inference, P. 111-112](https://mitpress.mit.edu/books/elements-causal-inference#:~:text=Elements%20of%20Causal%20Inference%20is,data%20to%20understand%20the%20world.)
4. [The Paper of How: Estimating Treatment Effects Using the
Front-Door Criterion](http://marcfbellemare.com/wordpress/wp-content/uploads/2019/08/BellemareBloemFDCAugust2019.pdf)
5. [Wikipedia's Average Treatment Effect](https://en.wikipedia.org/wiki/Average_treatment_effect)