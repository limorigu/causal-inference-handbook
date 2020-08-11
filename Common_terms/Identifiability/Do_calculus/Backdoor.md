Backdoor criterion
======

### Motivation

One of the main tools in the causal toolbox, where we attempt to draw causal conclusions (i.e. compute ![causal effect](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Causal_Effects/Causal_Effects.md) such as ATE, CATE, etc.) from observational data, in the presence of ![confounding](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Identifiability/Bias/Confounding.md). A confounder would be a covariate(s) which affects both the treatment itself and the outcome simultenously, thus "obscuring" the signal we might want to measure. Confounders are usually behind examples of ![entertaining spurious correlations](https://www.tylervigen.com/spurious-correlations), such as finding high positive correlation between eating ice cream and death occurances. While it is often tempting to think of correlation as implying a sense of causation, we also know from statistics classes we should NOT fall for it. While ice cream and death cases might co-occur, they both have the common cause of "hot weather", which acts as a confounder in this case. Imagine ice cream eating is denoted as X, and death occurance denoted by Y. Such obscuring via the confounder "hot weather" would imply P(Y|X) ≠ P(Y|do(X)). The LHS can be obtained from a simple regression (of the observed)Y\~X; the RHS is obtained in controlled experiments where we can set X to a certain value (e.g. make many people eat ice cream) and observe the subsequent values of Y (did rate of death increase?). In this short introduction, we would show however, that via the backdoor criterion we might still be able to recover P(Y|do(X)) from observational data, without relying on a contolled experiment setup where we can perform interventions physically.

The backdoor criterion is a graphical criterion which allows one to check whether there are any open, backdoor paths between X (some treatment of interest, e.g. taking a drug) and Y (some outcome of interest, e.g. survival). Note that, when confounding happens, there is an arrow into X on some path between X and Y - these are known as _backdoor paths_. In a sense, what the criterion is checking is whether confounding exists between X and Y, which could bias the estimation of causal effect when considering the simple observational P(Y|X); in the case of no confounding, the causal P(Y|do(X)) = P(Y|X); if confounding does exist, we will have to look for a valid adjustment set which could block the backdoor path from X to Y (blocking is defined via ![d-separation](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Do-Calculus/d-separation.md)).

### Definition

The formal definition of the backdoor criterion states:
> A set of variables Z satisfies the back-door criterion relative to an ordered pair of variables (Xi, Xj) in a DAG G if:
>(i) no node in Z is a descendant of Xi; and
>(ii) Z blocks every path between Xi and Xj that contains an arrow into Xi.
> Similarly, if X and Y are two disjoint subsets of nodes in G, then Z is said to satisfy the back-door criterion relative to (X,Y) if is satisfies the criterion relative to any pair (Xi, Xj) such that Xi∈X and Xj∈Y.

Condition (ii) gives the criterion its name: it is concerned with blocking paths which point at Xi. Since we are interested in the causal effect of X on Y, the notion of an arrow pointing at Xi can be visually thought of as a "backdoor", going "back" into Xi.

### Example and Intuition

Being a graphical criterion, it is most easily understood alongside a graphical, visual representation. A common toy example that shows the applicability of the criterion is the following. 

![backdoor_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/backdoor_DAG.jpg)

In this typical example, {X3, X4} would be a valid adjustment set, and so would {X4, X5}. Including either in the analysis would result in the blocking on the backdoor path. However, adjusting just for X4 would yield a biased estimate (because it might block the path Xi <- X4 -> Xj, but will open the currently blocked path Xj <- X3 <- X1 -> X4 <- X2 -> X5 -> Xj, since X4 is a collider on that path); similarly, adjusting for X6 would give a biased estimate because it would amount to blocking the path Xi -> X6 -> Xj, which actually constitutes what we want to measure. X6 is a mediator, i.e. part of the mechanism that facilitates the influence of Xi on Xj, and thus we should not adjust for it. 

After identifying the adjustment set via the Backdoor criterion, we can simply use the following Backdoor Ajustment theorem to recover the causal effect of X on Y: 
> If a set of variables Z satisfies the back-door citertion relative to (X,Y), then the causal effect of X on Y is identifiable and is given by the formula 
>P(y|do(x)) = \Sum_z P(y|x,z)P(z).

The backdoor criterion is one prototypical example of how to identify causal effects from observational data. However, it is a graphical criterion, i.e. it relies on knowledge of the underlying causal graph of the data generation process. The backdoor criterion might not always be immidiately applicable for a given graph, i.e. might not always find an adjustment set to deconfound a causal effect of interest. In such cases, ![the front-door criterion](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Do-Calculus/Frontdoor.md) might still apply, or the use of additional covaraites (intrumnetal variables, proxies) might be needed. A general framework for replacing causal quantities with observational ones is the do-calculus theorem.

### Further reading

For more, see discussion in [Causality 2nd edition](http://bayes.cs.ucla.edu/BOOK-2K/), Section 3.3.1; [A Generalized Backdoor Criterion](https://arxiv.org/pdf/1307.5636.pdf) 

Moreover, for backdoor blocking with minimal knowledge of DAG, see [Differentiable Causal Backdoor Discovery](http://proceedings.mlr.press/v108/gultchin20a.html)
