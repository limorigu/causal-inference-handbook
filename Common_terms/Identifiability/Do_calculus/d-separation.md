d-separation
============

Motivation
==========
d-separation is a fundemntal concept in the SCM, graphical flavour of causal inference, as well as in Bayesian nets more generally. It gives a systematic way to predict whether covariates represented by a causal graph will show dependence or independence in any dataset that is generated according to a particualr causal graph. The "d" part of the name thus reference to "dependence". To understand the concept better, we first need to have a quick introduction to the relationships between variables that make up a graph.

Introduction: confounders, mediators and colliders
=================================================
The fundamental building blocks of a causal graph, decribing every possible relationship between any three related variables, are the following:

Confounders (also related to the [Reichenbach's common cause principle, see principle 1.1 in Elements of Causal Inference](https://mitpress.mit.edu/books/elements-causal-inference#:~:text=Elements%20of%20Causal%20Inference%20is,data%20to%20understand%20the%20world.)): variables which are common causes of two others, i.e. for some random variables X, Y, Z, X <- Z -> Y. Confounders imply dependence between X and Y, X¬⫫Y, and yet conditional independence given Z, X⫫Y|Z. In some sources, this conditional indepepndence of the children X and Y given the common cuase parent Z is described as Z "screening off" X and Y from each other. Confounders are the main threats behind [Confounding Bias](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Bias/Confounding.md), and a common example can be if we try to explain the relationship between ice cream consumption (X) and number of death cases caused by drowning in pools (Y). While X and Y can show positive correlation, it is likely that the two have a lurking common cause behind both, hot weather (Z). As such, it is likely that we have the following structure Ice_creatm_consumption (X) <- hot_weather (Z) -> death_cases_in_pools (Y).

2. Mediators: variables in the causal graph that can thought of as the mechanism describing a relationship between two, more remotely associated variables, i.e. X -> Z -> Y. An example could be the process by which taking a medication might lead to some outcome, like reducing a headache. While a pill can indeed help us reduce headaches, it is through the chemical reaction the pill triggers that the headache is reduced, i.e. medication (X) -> chemical_recation (Z) -> Y. While Z again renders X and Y dependent, X¬⫫Y, conditioned on Z, the mechism, we once again loose the association between X and Y, i.e. X⫫Y|Z.

3. Colliders: when two seemingly unrelated phenomena, represented by random variables, are related by relationship to a third one, we see colliders (also called a v-structure or immorality, with a slight traditional family moralistic undertone, derived from the fact we are looking at a child node from two parent nodes which are not themselves adjacent). In other words, we look at a case where both some X and Y point at a Z, X -> Z <- Y. A common examle might be a study that aims to look at the occurance of two diseases, say cancer (X) and tuberculosis (Y). While the two might not be correlated in the general population, if we relate them by performing the study at a particular hospital (Z), we could be linking the two -- making them seem negatively associated when we condition on presence in hospital Z. Following this logic, we see that in this case, unlike the two previous ones, cancer (X) and tuberculosis (Y) might be marginally indepepndent, X⫫Y, and yet become dependent when conditioning on hospital presence (Z), X¬⫫Y|Z. This example is what constitutes [Berkson's paradox](https://en.wikipedia.org/wiki/Berkson%27s_paradox#:~:text=Berkson's%20paradox%20occurs%20when%20this,absent%20are%20not%20equally%20observed.).

Putting it all together: d-separation
=====================================

When trying to systemtically reason through bigger networks and graphs, where nodes are often conncected via more than one path, we can use the insights about dependence and independence above in a more formalized manner. That is where Pearl's d-separation comes in.

> A path p is blocked by a set of nodes Z, if and only if
> 1. p contains a chain of nodes A -> B -> C (i.e. B is a mediator) of a fork A <- B -> C (i.e. B is a confounder), such that the middle node B is in Z (i.e., B is conditioned on), or
> 2. p contains a collider A -> B <- C (i.e. B is a collider) such that the collision node B is not in Z, and no descendant of B is in Z.
> If Z blocks every path between two nodes X and Y, then X and Y are d-separated, conditional on Z, and thus are independent conditional on Z. 

With this definition, we can start to reason through cases where we would like to d-separate variables, and ones where we would like to maintain variables d-connected. For example, when studying a causal effect of interest, we would want to block paths with confounders, that could trick us into thinking some variable X causes another Y, where really their relationship is explained by a third common cause (just like ice cream consumption doesn't cause pool drownings in the example above). On the other hand, we would also not like to block mediation paths (e.g. when trying to assess the efficacy of a medication for reducing headache we *would* like to keep the mediating mechnism active, and not condition on it, such that the effect of medication taking on headache appearance will seem to disappear); and we would similalry not like to _open_ currently blocked paths with colliders in them, as when studying the relation between two diseases, we would not like to condition on a random variables, such as hospitalization, that would make the two seem related when in the general population they are not. 

d-sepeation underlies many topics in the graphical interpretation of causal inference, and features, for example, in the [Backdoor criterion](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Identifiability/Do_calculus/Backdoor.md) and [Frontdoor criterion](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Identifiability/Do_calculus/Frontdoor.md) for causal effect recovery/estimation.
 


Further Reading
====
1. [Pearl's d-separation without tears](http://bayes.cs.ucla.edu/BOOK-2K/d-sep.html#:~:text=d%2Dseparation%20is%20a%20criterion,ness%22%20or%20%22separation%22.)
2. [Richard Scheines's d-separation tutorial](https://www.andrew.cmu.edu/user/scheines/tutor/d-sep.html)
3. [Pieter Abbeel's d-separation video for Bayesian nets](https://www.youtube.com/watch?v=yDs_q6jKHb0)
4. d-seperation, chpater 2.4 in [causal inference in statistics: A Primer](http://bayes.cs.ucla.edu/PRIMER/)
5. For a slightly different flavour, see [Elements of Causal Inference, chapter 6, definition 6.1](https://mitpress.mit.edu/books/elements-causal-inference#:~:text=Elements%20of%20Causal%20Inference%20is,data%20to%20understand%20the%20world.)