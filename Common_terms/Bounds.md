# Introduction to Bounding of Causal Effects

## Motivation

In the case of unmeasured confounding, when identification of causal effects is not possible without further assumptions, we are still able to calculate bounds on the effect of interest. These are not to be confused with confidence intervals, which make a statement about the certainty of measured number. These bounds provide a lower and upper limit to where the causal effect will be found. It is expected to never be measured outside these bounds  (apart from random variability).

Commonly, these bounds are calculated via introducing so called "response function variable" formulation. Often, the bounds will include 0, such that the effect of interest could be negative or positive, i.e. the bounds are not too informative. Importantly, these bounds are completely free from assumptions.

Generally, adding further assumptions will tigthen the bounds, and often start exclude 0, i.e. the bounds become informative by giving a range that is exclusively positive or negative.

Response function formulations are easily explained via the Instrumental Variable model applied on the case of imperfect compliance, see the section on intuition.
