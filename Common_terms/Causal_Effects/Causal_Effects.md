Motivation
====
Causal Effects are the kind of estimates we are mostly after when performing causal inference -- they are the way we can quantify answers to questions such as :
1. "What is the effect of rain on pavemenet sliperriness?"
2. "How does a water provider effect the death rate of Cholera?" 
3. "Does Berkley's graduate admission process suffer from gender bias? And how would gender effects likelihood of acceptance?"

All of these questions are causal effect queries that are relevant for various famous case studies and exmaples in Causal Inference literature. These basic queries can be stated more precisely via the different types of causal effects that are surveyed in this section (including *Average* treatment effect, *Conditional* treatment effect, *Indiviual* treatment effect and more). Notice that most times in the relevant literature these causal queries would be defined in terms of effects of _treatments_. This pratice comes from medical and epidemiological domains, but captures a more basic fact about these effects -- they measure the outcome of _interventions_, _manipulations_ or _treatments_.

The main distinction between association measures from classic statistics, e.g. correlations, and causal effect estimation is that the former are involved with *observational* quantities, that simply occur in some pre-existing data, while the former deal with the outcomes of interventions carried out on a system, which allows us to distinguish between spurious correlations, that do not describe any causal relationships in the underlying data generation process, but just seem to be related in some specific sample from a specific system. Causal relationships, on the other hand, are likely to be more stable, across samples, environments of measurment, etc. Some classic failures of statistical analysis that does not account for this somehwat subtle difference are numerous, and range from Simpson's paradox (see short discussion in [causal inference in statistics: A Primer, section 1.2](http://bayes.cs.ucla.edu/PRIMER/) and longer discussion in [Causality 2nd edition](http://bayes.cs.ucla.edu/BOOK-2K/), ch. 6.1), to common failures of classifiers in generalization for Out of Distribution examples (see, for example [Invariant Risk Minimization](https://arxiv.org/abs/1907.02893)).

Definition
====
The formal difference between measurment of statistical predictions and causal effect estimation stems from the simple difference between what they represent. 

Traditionally, when training a classifier or a regression problem we ask questions of the form P(y|x), what is the probability some label is y, or some of outcome of interest is of level y, given that some feature, inputs, covariates are at the level x. 

Causal effect estimation would instead ask the following (following Pearl's do calculus notation), P(y|do(x)), i.e. what is the probability of an outcome y given that we carry out an intervention, where our features are set to some level x. Perhaps a more intuitive formulation would look like P(Y=y|X=x, do(Z=z)), what is the probability some outcome variable Y would be of level y, when X is kept at its observed value x, but we carried some intervention on some feature Z and set it to the value z. Causal effects can also be realized via slightly different notations in the Rubin-Neyman framework (aka potential outcomes framework, aka [Rubin Causal Model](https://en.wikipedia.org/wiki/Rubin_causal_model)).

Do statements are associated with Structural Causal Models, following the formulation of Judea Pearl. In order to compute the causal effect entailed by P(y|do(x)) we have to make some assumptions about our data generation process, and SCMs, or Structural Equation Models are one way to state those clearly, which would in turn allow us to compute causal effects, and even tell us how to reduce causal queries back into appropriate observational quantities (this process is related to entries in the section on identifiability). For more, see, e.g. [causal inference in statistics: A Primer, section 1.5](http://bayes.cs.ucla.edu/PRIMER/). Each SCM is associated with a graphical causal model, which are most commonly Directed Acylclic Graphs (DAGs), but do not have to be. Those graphs encode causal assumptions via the relations of nodes in the graph: if a node Y is a child of node X, then X is a direct cause of Y; if Y is a descendant of X, then X is a *potential* cause of Y. Those relationships also tell how to decompose joint distributions, such as P(x,y), into the correct marginal and conditional distributions that could be multiplied to obtain said joint. 

Intuition via Examples
=====
Such DAGs could help to reason through the computation of answers to the introductory questions above. Here are the associated DAGs with each one of those queries:

1. ![Rain_pavement_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Causal_effects/DAG_rain_pavement.png), as presented in [Graphical_causal_models_slides](https://ftp.cs.ucla.edu/pub/stat_ser/uai12-mohan-pearl.pdf), but used elsewhere multiple times in Pearl's work. 
2. ![Cholera_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Causal_effects/DAG_cholera.png), adapted from [Pearl's Book of Why, Ch. 7, P. 245-250](http://bayes.cs.ucla.edu/WHY/)
3. ![Berkeley_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Causal_effects/DAG_Berkeley.png), from [Pearl's Book of Why, Ch. 9, P. 309-317](http://bayes.cs.ucla.edu/WHY/) 

Further Reading
=====
See, for example, [causal inference in statistics: A Primer, section 3.1, P. 53-55](http://bayes.cs.ucla.edu/PRIMER/) 
This is meant to be a (very) introductory entry to causal effects and their usefulness. The further entries in this section will deal with specific examples of common causal effects of interest in the literature. Please refer to other entries in this handbook or the links included above for more information.
