Backdoor criterion
======

One of the main tools in the causal toolbox, where we attempt to draw causal conclusions (i.e. compute causal quantities such as ATE, CATE, etc.) from observational data, in the presence of confounding. A confounder would be covariate which affects both the treatment itself and the outcome simultenously, thus "obscuring" the signal we might want to measure. Such obscuring would imply P(Y|X) ≠ P(Y|do(X)), where the first term can be obtained from a simple regression of the observed Y\~X, while the second term is obtained in a randomized control trial, where the assignment of treatment X is randomized. In this short introducion, we would show however, that via the backdoor criteria we might still be able to recover P(Y|do(X)) from observational data, without relying on a randomized control trial (RCT).

The backdoor criterion is a graphical criterion which allows one to check whether there are any open, backdoor paths between X (some treatment of interest, e.g. taking a drug) to Y (some outcome of interest, e.g. survival). In a sense, what the criterion is checking is whether confounding exists between X and Y, which could bias the estimation of causal effect when considering the simple observational P(Y|X); in the case of no confounding, the causal P(Y|do(X)) = P(Y|X); if confounding does exist, we will have to look for a valid adjustment set which could block the backdoor path from X to Y (blocking is defined via d-separation).

The formal definition of the backdoor criterion states:
> A set of variables Z satisfies the back-door criterion relative to an ordered pair of variables (Xi, Xj) in a DAG G if:
(i) no node in Z is a descendant of Xi; and
(ii) Z blocks every path between Xi and Xj that contains an arrow into Xi.
> Similarly, if X and Y are two disjoint subsets of nodes in G, then Z is said to satisfy the back-door criterion relative to (X,Y) if is satisfies the criterion relative to any pair (Xi, Xj) such that Xi∈X and Xj∈Y.

Condition (ii) gives the criterion its name: it is concerned with blocking paths which point at Xi. Since we are interested in the causal effect of X on Y, the notion of an arrow pointing at Xi can be visually thought of as a "backdoor", going "back" into Xi.

Being a graphical criterion, it is most easily understood alongside a graphical, visual representation. A common toy example that shows the applicability of the criterion is the following. 

![backdoor_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/backdoor_DAG.jpg)

In this typical example, {X3, X4} would be a valid adjustment set, and so would {X4, X5}. Including either in the analysis would result in the blocking on the backdoor path. However, adjusting just for X4 would yield a biased estimate (because it might block the path Xi <- X4 -> Xj, but will open the currently blocked path Xj <- X3 <- X1 -> X4 <- X2 -> X5 -> Xj, since X4 is a collider on that path); similarly, adjusting for X6 would give a biased estimate because it would amount to blocking the path Xi -> X6 -> Xj, which actually constitutes what we want to measure. X6 is a mediator, i.e. part of the mechanism that facilitates the influence of Xi on Xj, and thus we should not adjust for it. 

After identifying the adjustment set via the Backdoor criterion, we can simply use the following Backdoor Ajustment theorem to recover the causal effect of X on Y: 
> If a set of variables Z satisfies the back-door citertion relative to (X,Y), then the causal effect of X on Y is identifiable and is given by the formula 
P(y|do(x)) = \Sum_z P(y|x,z)P(z).

The backdoor criterion is one prototypical example of how to identify causal effects from observational data. However, it is a graphical criterion, i.e. it relies on knowledge of the underlying causal graph of the data generation process. The backdoor criterion might not always be immidiately applicable for a given graph, i.e. might not always find an adjustment set to deconfound a causal effect of interest. In such cases, the front-door criterion might still apply, or the use of additional covaraites (Intrumnetal variables, proxies) might be needed. A general framework for replacing causal quantities with observational ones is the do-calculus theorem.