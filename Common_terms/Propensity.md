'Probability of treatment'. Propensity stems from the 'propensity score' E_i = Pr(Z_i = 1 | X_i). Probability of treatment being 1 given the value of the covariates. It serves as a balancing factor -- we can retrieve similar distributions of the covariates in the treated and untreated groups conditioned on the propensity score. Thus we can compare sets of subjects that have the same propensity scores, as they will have very similar distributions over the covariates between the treated and the untreated groups. In RCTs it is known, and crafted by the study designer; in observational studies it is estimated, usually using logistic regression, but sometimes via bagging or boosting as well.

For more see https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3144483/

Most issues with that are:
- missing overlap between treatment and control
- extreme weights e.g. close to one or zero
- Positivity violations, i.e. some confounder combinations were not observed (either because small sample size or systematic impossibility)
