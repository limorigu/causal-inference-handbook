Instrumental variables (IVs)
============================

### Motivation

Instrumental variables are one of the most well known tools to achieve identifiability of causal effect under unobserved confounding. It is commonly used throughout economics (e.g., [Wright 1928](https://books.google.co.uk/books?id=hig5AAAAMAAJ&source=gbs_book_other_versions); [Reiersøl 1945](https://books.google.co.uk/books/about/Confluence_analysis_by_means_of_instrume.html?id=lG3wZwEACAAJ&redir_esc=y)), epidemiology (e.g. [Hernan and Robins 2006](https://cdn1.sph.harvard.edu/wp-content/uploads/sites/1268/2013/01/hernan_epidemiology06.pdf), [Greenland 2000](https://academic.oup.com/ije/article/29/4/722/765560)), social sciences (see reviews in [Bollen 2012](https://www.annualreviews.org/doi/pdf/10.1146/annurev-soc-081309-150141), [Dunning 2012](https://www.cambridge.org/core/books/natural-experiments-in-the-social-sciences/instrumentalvariables-designs/2980B3E79D3A94A85D58E4C362EA5224)) and other fields concerned with the estimation of causal effects. The main idea behind IVs is intuitive -- they can be thought of as an alternative to a coin flip in a randomized experiment, in the sense that they are a cause of a treatment of interest, but are conditionally independent of the outcome given the treatment and all possible confounders. As such, they act as a treatment assignment that is not affected by confounders, which allows us to recover the causal effect of interest. 

### Definition
There are many explanations and examples that could help elucidate IVs further, but in most versions they need to adhere to the 3 following conditions:
1. **Relevance** infromally W ¬⫫ X. More formally P(X|Z,W) is not constant in W (i.e. the IV W must be associated with the treatment X)

2. **Exclusion** W ⫫ Y | X, {Z,U}, “W does not affect Y except through its potential effect on X“

3. **(marginal) Exchangeability** W and Y have no common causes W ⫫ Y | do(W=w), do(X=x). Could also be thought of as W ⫫ U | Z

The classic DAG to describe such a system would look like the one below.

![IV DAG](https://github.com/limorigu/causal-inf-handbook/blob/master/img/IV.png)

### Intuition and Further Reading

Different definitions of instrument variables through slight different perspectives are offered, among many, by Pearl ([Causality 2nd edition](http://bayes.cs.ucla.edu/BOOK-2K/), ch.8, P. 274), Peters, Janzing and Schoelkopf, ([Elements of Causal Inference](https://mitpress.mit.edu/books/elements-causal-inference#:~:text=Elements%20of%20Causal%20Inference%20is,data%20to%20understand%20the%20world.), P. 176) and Hernan and Robins ([Causal Inference: What If](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/), Chapter 16, in particular technical point 16.1). 

Instrumental variables are featured in the famous story of John Snow and the Cholera outbreak in mid-19th century London, in the introduction to deepIV paper (see the example of flight ticket pricing under possible observed confounding of holiday and unobserved confounding of conferences, and a possible Instrumental variable of interest can be oil prices (which affect ticket pricing but not purchasing or any of the confounders). 

Instrumental variables can then be used to recover causal effects, following the logic of randomized control trials. For applications using IVs explicitly see e.g. [deepIV](http://proceedings.mlr.press/v70/hartford17a/hartford17a.pdf), [IV regression](Common_terms/Identifiability/Doubly_robust.md).

