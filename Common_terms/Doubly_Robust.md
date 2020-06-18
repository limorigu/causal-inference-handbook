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

