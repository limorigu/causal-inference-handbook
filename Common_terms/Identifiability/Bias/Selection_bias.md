Selection bias 
==============
Bias associated with the data gathering process, rather than the confounding bias associated with the treatment assignment itself (i.e. sampling based bias, rather than “data generation” bias, i.e., confounding bias). It represents factors that might affect which samples we obtain, such that they do not accurately reflect the underlying data generation process. In other words, it pertains to preferential selection of units of analysis in ways that could have a “systematic explanation”, that is however absent from the dataset we end up observing. 

Intuition and Examples
===
For example, the famous poll failing of the magazine [Literary Digest](https://en.wikipedia.org/wiki/The_Literary_Digest) was a classic case of selection bias (as well as non-response bias) -- while the pollsters believed they were collecting the political leanings of the “public”, they ended up collecting data about subscribers to a magazine, which reflected a richer, more well-read segment of the population, than the real, general, public that goes to vote.

# TODO: add two graphical examples, possibly to the literary digest case, and perhaps to another Berkson's paradox of sampling patients from hospitals. Take another look and the data-fusion problem paper, and potentially others, both for examples and to add to further reading.

Pearl and Barenboim delineate a strategy for identification of causal effects in the presence of selection bias, see the section _Sample Selection Bias_ in [Causal inference and the data-fusion problem](https://www.pnas.org/content/113/27/7345.short). The main idea is to include a selection indicator S and embed it appropriately in the structural causal model M. Thus, a user can then judge whether selection is conditionally independent of the effect of interest (in which case there is not threat to identification), or if additional methods can apply (e.g. see Definition 4, Selection backdoor criterion, in [Causal inference and the data-fusion problem](https://www.pnas.org/content/113/27/7345.short)).  

Further Reading
====
1. [Bareinboim and Pearl's inference and the data-fusion problem](https://www.pnas.org/content/113/27/7345.short) which considers (sample) selection bias and general strategies to address it. See the section headed "Sample Selection Bias".
2. [Wikipedia's Selection Bias entry](https://en.wikipedia.org/wiki/Selection_bias)