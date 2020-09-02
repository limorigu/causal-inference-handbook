One of the common assumptions in causal inference. Essentially the assumption is that for each value of covariate L=l, the probability of receiving all levels of treatment is greater than 0, i.e. P(A=a|L=l) for all a ∈ A,l ∈ L. In practice, we need this condition to hold to have a distribution of the effect of interest for a given treatment and covariate level. 

If positivity is violated (i.e. we do not observe a treatment level of interest for some subsection of the population), it could be for statistical or random missing information reasons, or a mechanistic or structural reason. Structural missingness is often much more problematic. 

In RCTs, we control assignment to different treatments (via coin flipping or the equivalent thereof), which can ensure positivity holds.

For more, see Technical Point 2.3, Hernán MA, Robins JM (2020). Causal Inference: What If. Boca Raton: Chapman & Hall/CRC. https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/
