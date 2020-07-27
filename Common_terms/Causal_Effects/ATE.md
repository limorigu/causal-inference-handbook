Motivation
====
It is often the case that causal effect on interest can be stated as average-effect statements, when we want to ask not about the effect of a treatment on one specific instance in a dataset, but rather on an *on average* effect, across the dataset. Such statements are usually spelled out via the Average Treatment Effect Definition. 

Definition
====
> ATE = E[Y|do(X=1)] - E[Y|do(X=0)]
To spell this out a little more, ATE tell us what is the average causal effect, or difference between the average effect of taking a treatment (or carrying out an intevention setting the variable treatment to 1), vs the average effect on no taking a treatment (and thus setting the variable treatment, via an intervention, to 0).

The same definition also often appears as Average Causal Effect (for example, in Peters, Janzig and Schoelkopf's elements of causal inference, see below).

Intuition and Examples
===
This is a common query in causal inference, as it can give is a rough idea of the effect of interventions. It also follows the logic of Randomized Control Trials closely: it tells us of the difference in expectation of some outcome of interest (such as the state of a disease), in some group that has taken a treatment vs. in a *control* group, that hasn't taken the treatment (e.g. some drug under test). 

Notice that the use of do-notation above is crucial for this RCT-like formulation: we consider the case where a randomized process led to such an intervention, assigning some individuals to a group that takes the drug, vs. other to the control group that doesn't take the drug. This intervention makes sure there are no lurking confounders, that might explain the presence of certain indiviuals in one of the groups, due to some other characteristic they share (e.g. if the assignment to the treatment group is not random, but is associated with a higher socio-economic status, that in terms might lead some doctors to be more lenient with subscriptions of drugs, as well as effect the likelihood of recovery via other factors such as diet, excercise or stress levels) we can no longer make causal conclusions about the efficacy of a drug from such a dataset!

Thus, the average treatment effect gives us a simple, crude estimate of the effect of some intervention on some outcome, and crucially does so via the do operator, and not through simple observed quantities X=0 or X=1.

The notion of ATE can be extended to continuous treatment, but requires a definition of a baseline to take the difference against.

Further Reading
====
See more at:
1. [Causal Inference: What If, Ch. 1.2](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/)
2. [MIT's Economics department's summary, P. 2](https://economics.mit.edu/files/32)
3. [Elements of Causal Inference, P. 111-112](https://mitpress.mit.edu/books/elements-causal-inference#:~:text=Elements%20of%20Causal%20Inference%20is,data%20to%20understand%20the%20world.)
4. [The Paper of How: Estimating Treatment Effects Using the
Front-Door Criterion](http://marcfbellemare.com/wordpress/wp-content/uploads/2019/08/BellemareBloemFDCAugust2019.pdf)
5. [Wikipedia's Average Treatment Effect](https://en.wikipedia.org/wiki/Average_treatment_effect)