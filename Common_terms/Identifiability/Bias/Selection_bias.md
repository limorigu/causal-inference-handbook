Selection bias 
==============
Bias associated with the data gathering process, rather than the confounding bias associated with the treatment assignment itself (i.e. sampling based bias, rather than “data generation” bias, i.e., confounding bias). It represents factors that might affect which samples we obtain, such that they do not accurately reflect the underlying data generation process. In other words, it pertains to preferential selection of units of analysis in ways that could have a “systematic explanation”, that is however absent from the dataset we end up observing. 

For example, the famous poll failing of the magazine [Literary Digest](https://en.wikipedia.org/wiki/The_Literary_Digest) was a classic case of selection bias (as well as non-response bias) -- while the pollsters believed they were collecting the political leanings of the “public”, they ended up collecting data about subscribers to a magazine, which reflected a richer, more well-read segment of the population, than the real, general, public that goes to vote.

Selection bias meets DAGs and causal inference
==============================================

A natural follow up question to ask before carrying out a statistical or causal analysis is whether the threat of selection bias is present in a given dataset. And if the answer is positive, is the analysis necessarily doomed? Fortunately, the answer is no, and DAGs, as we have seen in the case of [confounding](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Identifiability/Bias/Confounding.md), can help determine when and how can conditional probabilities such as P(y|x), as well as interventional ones such as P(y|do(x)) can be recovered, even under selection bias. 

The basic idea behind the process consistes of two parts: 1) representing the selection process which determines the sampling of points as a node in the graph (usually with the character S, often as an emphasized node, e.g. with two encircling lines, rather than the usual one. See example below); 2) Once S is represented in the data generation DAG, we can use the rules of [d-separation](https://github.com/limorigu/causal-inf-handbook/blob/master/Common_terms/Do-Calculus/d-separation.md) to check if Y \ind S | X, or whether such independence can be achieved conditioned on an additional valid set Y \ind S | X, C. We will not go in to great detail of all possible scenarios and sets for which this condition can hold (for those, refer to the highly recommended [Bareinboim et al. 2014](https://ftp.cs.ucla.edu/pub/stat_ser/r425.pdf)). 

To elucidate these points, let's consider the following running example. Assume we want to measure the correlation of education and income, and later on perhaps estimate the causal effect of education level on income level. However, it is very likely that in a study that's any less than maticulously planned, we will be exposed to selection bias. Let us consider two possible scenarios matching this description, and see when we can recover from selection bias and when we cannot. 

First, consider the following DAG. The covariate X stands for Education level, Y represents income level and S will be the selection indicator to the sample (when S=1. S=0 will correspond to unavailable datapoints). Assume, for example, that we only collected data on university campuses, or that polling is done via a newspaper that is often read by people of a cerain education level. 

![DAG_recoverable](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Selection_bias/Selection_bias_recoverable.png)


In this DAG, we can easily tell from first glance that indeed Y \ind S | X. Using this fact, we can easily state the P(y|x) = P(y|x, S=1), which immidiately means we managed to recover P(y|x) from this DAG (i.e. S-recoverable, in the language of Bareinboim et al. 2014). Now consider the slightly altered DAG below. In this scenario, we are still interested in the same conditional distribution, but this time income level Y is the ancestor of S, instead of education level X. This could happen if sampling is affected by income and not education, for example, if we have reason to believe we tend to get responses from high earners, as they are more willing to participate in a survey considering their income. 


![DAG_non_recoverable](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Selection_bias/Selection_bias_non_recoverable.png)

As we can easily tell from this DAG, we no longer have the indpendence of the sampling node S from Y given X (Y \not_ind S | X). Thus, we cannot recover P(y|x) from this DAG. 

Another immidiate follow up question in the context of causal inference would be, when can we recover the interventional distribution P(y|do(x)) from a DAG. Essentially to answer this question positively, we need to verify that we can decondound the causal effect, while also ensuring Y \ind S | X (or given X and an appropriate set C). In the case of the first DAG above, as X and Y are not confoundeda anyway, we can get interventional S-recoverability easily, as P(y|do(x)) = P(y|x).  However, in most cases S-recovarability will not be so immidiately apparent, and so Bareinboim, Tian and Pearl suggest an extention to the backdoor criterion for the selection bias setting.


For formal theories and complete characterization of when S-recoverability exists and when not, see [Bareinboim et al. 2014](https://ftp.cs.ucla.edu/pub/stat_ser/r425.pdf)) or the section _Sample Selection Bias_ in [Causal inference and the data-fusion problem](https://www.pnas.org/content/113/27/7345.short). In short, these works cover conditions for recovery of conditional probabilities and interventional probabilities in the presence of selection bias, following the sturcture suggested by the running example above. That is, 1) when no external, population level samples for additional covariates exist 2) when such external measures exist, and 3) extension of the backdoor criterion to the selection bias case, i.e. selection backdoor criterion and selection backdoor adjustment.

Further Reading
====
1. [Bareinboim et al. 2014, Recovering from Selection Bias in Causal and Statistical Inference](https://ftp.cs.ucla.edu/pub/stat_ser/r425.pdf)
2. [Bareinboim and Pearl's inference and the data-fusion problem](https://www.pnas.org/content/113/27/7345.short) which considers (sample) selection bias and general strategies to address it. See the section headed "Sample Selection Bias".
3. [Wikipedia's Selection Bias entry](https://en.wikipedia.org/wiki/Selection_bias)