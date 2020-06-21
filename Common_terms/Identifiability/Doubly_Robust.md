Doubly Robust methods
=====================
When trying to estimate the average causal effect of a treatment from observational data we can employ multiple approaches, including IP weighting or standardization. IP weighting will require us to model P(A=a, C=0 | L), which can be estimated via two logistic regression models for (A=a | L) and (C=0 | A=a, L). Standardization on the hand relies on modelling the conditional means E[Y| A=a, C=0, L=l], which can be estimated for example with a parametric linear regression model. However, given that these models are estimations, and some bias will likely exist for all of them, they are likely to differ (if no bias exist, both methods will get at the same estimation values). 

Doubly robust estimators are trying to overcome this issue -- it is enough for the model of the outcome Y to be unbiased, or for the model of the treatment A to be unbiased -- i.e. doubly robust estimator consistently estimates the causal effect if at least one of the two models is correct. One example of doubly robust estimator is proposed in [Bang and Robins (2005)](https://onlinelibrary.wiley.com/doi/10.1111/j.1541-0420.2005.00377.x) (see Fine point 13.2 in [Causal Inference: What If](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/), 2020). All doubly robust estimators involve a correction of the outcome model by a function that involves the treatment model (the first-order influence function).

Another illustrative description is given in [Funk et al. 2011](https://academic.oup.com/aje/article/173/7/761/103691):
> Doubly robust estimation combines a form of outcome regression with a model for the exposure (i.e., the propensity score) to estimate the causal effect of an exposure on an outcome. When used individually to estimate a causal effect, both outcome regression and propensity score methods are unbiased only if the statistical model is correctly specified. _The doubly robust estimator combines these 2 approaches such that only 1 of the 2 models need be correctly specified to obtain an unbiased effect estimator._

Example: 2 step regression (or IV regression)
=====
Extension to OLS under structural equations framework. Can be useful when a dependent variable’s error term is correlated with the independent variable, or when there are feedback loops in the model. One illustrative example can be seen here, from econometrics, https://fmwww.bc.edu/EC-C/F2012/228/EC228.f2012.nn15.pdf, where a researcher is interested in fitting the model to compute wage (or log(wage)), and assumes it is correctly specified as 
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg1.png)

But ability is a latent variable. We can try to add it to the error term e and create a new error variable u. However, now if ability and education are correlated, we created a problem that will lead to inconsistent estimation. 

Instead, we can use an instrumental variable z, which needs to be correlated with education, but independent of u (we can’t check the latter b/c u is unobserved, but we can check the former by simply regression education on z and seeing the fitted weight on z is non-zero. 

Having such a z, we can now perform the original regression we were interested in in 2 steps:
1. Fit a first regression, where
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg2.png)
2. Replace education in the original with its estimator using the instrumental variable z,
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg3.png)

One way to think of why this should work is that we essentially want to use the instrument variable to potentially deconfound latent variables. One way to see this is, that if writing the equation with the latent variable again 
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg4.png)

We can now take the covariance of each term in this equation with the instrument Z
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg5.png),
but since the last term is by definition 0, we can find the solution to β1 simply through 
		![log-wage](https://github.com/limorigu/causal-inf-handbook/blob/master/img/doubly_robust/2stepreg6.png) 
and thus avoid the need to use U.

Another recent example for a 2-step regression which uses IV regression as one end of its interpolation is [anchor regression](https://arxiv.org/abs/1801.06229).

See also https://jstor.org/stable/24310144?seq=1#metadata_info_tab_contents

