Frontdoor criterion
======

### Motivation

As mentioned in [Backdoor Criterion](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Identifiability/Backdoor.md), not all causal effects for all graphs can be uncovered using the Backdoor Criterion. The Backdoor Criterion, as well as the Frontdoor Criterion, formalize specific common DAGs, and suggest immidiate graphical criteria for the estimation of a causal effect on interest, some P(Y=y|do(X=x)). The [Frontdoor criterion](https://academic.oup.com/biomet/article-abstract/82/4/669/251647) is yet another tool in our causal estimation toolbox, which allows one to extract a causal effect easily given a certain type of DAG. The archetype DAG on which the frontdoor criterion would find an adjustment set for a causal effect estimation would be the following:

![frontdoor_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/frontdoor_DAG.png)

Suppose X is some intervention or treatment, we are interested in its influence on an outcome Y, and U is an _unobserved_ confounder. This time, note, we also have Z, a mediator between X and Y, which will help us carry out our causal effect estimation. 

We cannot simply apply the backdoor criterion in this case because U is unobserved, and thus we cannot use it for adjustment. But not all is lost just yet! We can apply a couple of imtermediate steps that follow immidiately from the DAG. In fact, both steps will be applications of the backdoor criterion:

1. We first notice that the effect of X on Z is easily identifiable: there is no backdoor path between X and Z, and thus P(Z=z|X=x) = P(Z=z|do(X=x)). Thus, we can say the null set is a valid adjustment set to recover P(Z=z|do(X=x)).
2. Next, we can apply the backdoor criterion again, this time to recover P(Y=y|do(Z=z)). Looking at the DAG, we can tell that we can use X in order to block the backdoor path between Z and Y, Z <- X <- U -> Y. Thus, we get P(Y=y|do(Z=z)) = Σ_x P(Y=y|Z=z, X=x)P(X=x)

We now have two causal effects that make up the path we are actually interested in. Thus, we can combine our previous estimations to get

P(Y=y|do(X=x)) = Σ_z P(Y=y|do(Z=z))P(Z=z|do(X=x)) = Σ_z P(Z=z|X=x) Σ_x' P(Y=y|Z=z, X=x')P(X=x'), which is what we sought out to get. 

### Definition 
Formally, the Front-door criterion states:
> A set of variables Z is said to satsify the front-door criterion relative to an ordered pair of variables (X,Y) if
> 1. Z intercepts all directed paths from X to Y. 
> 2. There is no unblocked path form X to Z.
> 3. All backdoor paths from Z to Y are blocked by X.

And the Front-door adjustment would simpy follow the procedure we carried out above.
> If Z satisfies the front-door criterion relative to (X,Y) and if P(x,z) > 0, then the causal effect of X on Y is identifiable and is given by the formula
> P(Y=y|do(X=x)) = Σ_z P(z|x) Σ_x' P(y|z, x')P(x')

### Intuition and Example

To see why the above might be true, let's look once again at the classic frontdoor DAG above. We can denote the joint it represents as P(X, Z, Y, U), and we would like to obtain P(Y|do(X)). If we actually carry out such intervention on X, we would end up with the following DAG, post-intervention:

![frontdoor_DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/frontdoor_DAG_intervened.png)

where the joint is denoted as P̂(X, Z, Y, U). From this new DAG, we would actually have P(Y|do(X)) = P̂(Y|X). Note, also, that we can get to P̂(Y|X) via marginalizing Z out in the following P̂(Y|X) = Σz P̂(Y|Z)P̂(Z|X).

Now, observe the following:
P̂(Y|Z) = P(Y|do(Z)),
P̂(Z|X) = P(Z|do(X)), 
And so 
P(Y|do(X)) = Σz P(Y|do(Z))P(Z|do(X)) <=> P̂(Z|X) = Σz P̂(Y|Z)P̂(Z|X). 

We have now shown the equivalence of these statements between the original graph and the intervened graph, which gets exactly at the intuition behind the frontdoor criterion, which levarage the mediator Z, to essentially apply the backdoor criterion twice, and get to P(Y|do(X)).

### Further Reading
The criterion and some examples of its usefulness are included in [Pearl's Causality, 2nd Edition, Section 3.3.2-3.3.3](http://bayes.cs.ucla.edu/BOOK-2K/), as well as in [causal inference in statistics: A Primer, section 3.4](http://bayes.cs.ucla.edu/PRIMER/), and [Causal diagrams for empirical research](https://academic.oup.com/biomet/article-abstract/82/4/669/251647).

For the general framework for the identification of causal effects, i.e. measuring the effects of interventions, see Pearl's Causality, 2nd Edition, Section 3.4](http://bayes.cs.ucla.edu/BOOK-2K/).


