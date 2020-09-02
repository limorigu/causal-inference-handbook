Introduction to Bounding of Causal Effects
==========================

Motivation
=========

In the case of unmeasured confounding, when identification of causal effects is not possible without further assumptions, we might ask: Can we still squeeze some information out of observational and experimential measurement data?

This answer is yes. We can calculate bounds on the effect of interest. For example, if I want to know how effective aspirin is at removing headaches, and I face unmeasured confounding in my data, I can still calculate bounds on the effect and they might look like this:

> Lower bound: 0.04

> Upper bound: 0.42

With these bounds, I cannot tell what the exact effect of aspirin on headaches will be, BUT I can say that it will definitely be positive, which is a piece of information I can still act on as a doctor.

These bounds are not to be confused with confidence intervals, which make a statement about the certainty of a measured variable of interest. These causal bounds provide a range where the causal effect will be found, i.e we expect the effect to never be fall outside these bounds (apart from random variability).

Definition
==========

Commonly, causal bounds are calculated via introducing so called _response function variables_ (RFVs). Response function formulations have a simple and intutive explanation via the Instrumental Variable model, in the context of imperfect compliance, see the *Intuition: Causal Bounds with imperfect compliance via the insturmental variable model*.

Put succinctly, the RFVs are then used to parameterize the causal model in a more 'granular' or 'fine' way, taking into account the different possibles response of a variable to its ancestors. This yields a linear program, for which, then the objective, representing the causal effect of interest, is optimized for its maximum and minimum value, i.e. the upper and lower bound of the causal effect.

Here, we assume a Structural Causal Model as stated for example by Pearl.

Put succinctly, the RFVs are then used to parameterize the causal model in a more 'granular' or 'fine' way, taking into account the different possibles response of a variable to its ancestors. This yields a linear program, for which, then the objective, representing the causal effect of interest, is optimized for its maximum and minimum value, i.e. the upper and lower bound of the causal effect.

Here, we assume a Structural Causal Model as stated for example by Pearl.

Key argument: (based on Wu et al. 2019)

Consider a endeogenous variable V, with its
* endogenous parents PA_V and
* exogenous parents U_V and
* its associated structural function v = f_V(pa_V, u_V)


U_V can be any variable of any type, with and any domain size. f_V can be any function.

As described in the subsection on Intuition, for each value of U_V, the functional mapping from PA_V to V is a definite deterministic response function, such as denying a prescription or any of the other three. Therefore, each value of U_V can be associated with a unique functional response.

*Consequence:* Despite a potentially infinite domain size of U_V, the number of deterministic response functions is predefined by the domain sizes of PA_V and V itself. That is, there is a limited number of ways the variable V can react to its parents, such that we can fully enumerate them, i.e. make a complete list of them.

*The response function variable is defined as:*

R_V = {0, ..., N_V -1}

N_V = |V|^|PA_V| is the absolute number of response function states that map all possible values of PA_V to V.

A specific value r_V of R_V then represents a specific response of V to its inputs. The trick is to now relate the causal model with these response functions.

*Expressing P(V) as a linear function of P(R)*

P(V) = Σ_r P(r) ∏_{v ∈ V} I(v; pa_V, r_V)

For example for an IV model, and the treatment variable X, we have:

P(Z,X) = Σ_r P(r_Z, r_X) I(z; r_Z) I(x; z, r_X)

where the Indicator I(v; pa_V, r_V) function indicates whether the response function in question contributes to the probability state.

Together with the probabilit simplex, we can then construct a linear program. The objective function can be constructed in the same way, with response functions, to represent the causal effect of interest. Minima and maxima of this objective then constitute the lower and upper causal bound. The linear program practically identifies the 'worst' case causal effect and the 'best' case causal effect and together the possible range of causal effects.

#### Further notes

Often, the bounds will include 0, such that the effect of interest could be negative or positive, i.e. the bounds are not too informative.

Importantly, these bounds are completely free from assumptions. Adding further assumptions will tigthen the bounds, and often start to exclude 0, i.e. the bounds become informative by giving a range that is exclusively positive or negative. For example, assuming Monotonicty, i.e. that there are no defiers, can signifcantly increases the usefulness of the bounds. Bounds calculated with monotonicity obviously are then based on the assumption of no defiers, which often is hard to verify.

Response function variables are not the only way to calculate causal bounds. Ramsahai describes in this PhD Thesis a way of calculating bounds without the use of response functions, see *Further Reading*. In his own words: "It has been shown that the bounds exist by direct use of the properties of probability distributions, without relying on the additional assumptions associated with potential outcomes"

Intuition
=========

Bounding of causal effects with response functions is most easily understood via the example of imperfect compliance evaluated via an instrumental variable model.

### The problem of 'imperfect compliance'

When doctors prescribe aspirin, but patients do not stick to their prescription, i.e. what their doctor told them to do, we face the problem of 'imperfect compliance'. For example, if a doctors sees 100 patients per week, and tells 50 of them to take aspirin, but only 40 take aspirin as prescribed, then we have 10 patients that do not comply, i.e. non-compliers (50-40=10).

The problem of 'imperfect compliance' is that we cannot calculate the causal effect of aspirin on relieving headaches. If we treat the patients with a prescription Z and measure the outcome Y of this aspirin, the effect will be biased as we will evaluate 10 patients as having received the treatment, when in fact they did not as they did not comply to the prescription.

One could say, that we instead shall keep track of compliance itself, i.e. who ends up taking the aspirin. For example, we can calculate the effect of taking aspirin, i.e. compliance X, onto the outcome Y. But in reality, we there will be'reasons' why people did not comply to the doctor's prescription. If these reasons also influence the effectivenes of the drug for a patient, then we will face confounding of X and Y, i.e. there is a confounding factor U, that influences both the compliance to the prescription X and the outcome Y of taking the drug. If we have complete knowledge of these reasons U we can adjust for the via the backdoor criterion. If we do not know all the reasons, we are facing unmeasured confounding, which is the more realistic case.

The instrumental variable model, as described next, will help with this unmeasured confounding. It is a popular method for handling unmeasured confounding.

### Causal effects with imperfect compliance via the insturmental variable model

While the instrumental variable model (IV model) can be applied to all kinds of problems of confounding, we will continue to look at it from the perspective of imperfect compliance.

The instrumental variable models helps adjust for the bias introduced by imperfect compliance via unmeasured confounding. Instead of looking at the compliance X and the outcome Y, we also take into account the prescription of the patients, denoted by X.

There are three conditions that a IV model needs to meet for unbiased inference. These conditions concern the actual Instrumental Variable, commonly denoted as Z.

The IV model follows the following structure:

X = g(Z, U), i.e. compliance to aspiring prescriptions is influenced by the actual prescription Z and other factors U

Y = g(X, U), i.e. outcome of aspirin treatment is influenced by taking aspring (complying to aspiring prescriptions)

A variable is considered an IV if it fulfills the following conditions:

1. *Unconfounded Instrument:* Z is independent from confounders (measured and unmeasured) U
2. *Relevance:* Z has information on X
3. *Exclusion (of the IV as part of all variables influencing Y):* Given X and U, Y is independent of Z

**Intution:** The treatment X is confounded with the outcome Y, so calculating the effect from X on Y will be biased by the confounders.
* What if we had an additional variable, let us call it Z, that has information on X, i.e. a variable that moves together with it, BUT is not confounded with Y?
* Then it can 'jump in' for X and 'substitute' for it during the effect calculation.
* If Z and X have similar movements, then the effect of Z on Y should get quite close to the effect of interest of X on Y.
* The only thing we then need to watch out for then, is that Z does influence Y directly, but only 'through' X.

Summing up: Z needs to have information on X (Relevance), not be confounded with Y via confounders U (Unconfoundedness) and, finally, not influence Y directly (Exclusion Criterion)

### Causal BOUNDS with imperfect compliance via the insturmental variable model
So, how does the IV model applied to the problem of imperfect compliance relate to causal bounds?

*Reminder:*
The doctors prescribes aspiring (Z=1) or not (Z=0).
The patients ends up taking the aspiring (X=1) or not (X=0).
We can separate the possible type of responses of patients into *4 groups:*

![response_table](https://github.com/limorigu/causal-inf-handbook/blob/master/img/response_table.png)

*In words:*
Always Deniers never take aspirin, under any circumstances, with or without prescription, i.e. X=0 ('hardcoded')
Compliers always follow the prescription of the doctor, i.e. X=Z
Defiers always defy the prescription of the doctor, always do the opposite i.e. X=!Z (=1-Z)
Always Takers always take aspiring, regardless of the prescription, i.e. X=1
Hence, the problem of patients not abiding to prescription is called the problem of imperfect compliance, as some of the patients fall out of the group of compliers into any of the other three. While Always Deniers are not a problem if they were not given a prescription, as they behave as the doctor prescribed, our calculation of a causal of effect of taking aspirin (X) onto the outcome of reducing headaches (Y) will always be biased by patients that are Defiers.

_Core point:_ These four groups of patients give us a exhaustive and complete list of all possible reactions of patients to their prescription Z. Which group they fall in, is influenced by the confounders U. For example, scientific scepticism might lead a patient to Always Deny. Therefore, if the confounder U determines which of the four groups a patient falls in, we can separate U into 4 regions, where each region indicates which group a patient is in. That is, we can replace U with a variable R, that has 4 states (0,1,2,3 for the four groups) which indicate how the patient should *respond* to the value of Z, i.e. with what kind of *function* the patient shall process the prescription. This variable R, representing the influence of U, is called a *response function variable*.

<!---The section on the Definition above will explain the remaining parts for calculating the bounds.--->

Further reading
===============
1. *Overview:* This post by Pearl from April 2020 has a nice interactive graph that visualises bounds: [Which Patients are in Greater Need: A counterfactual analysis with reflections on COVID-19](http://causality.cs.ucla.edu/blog/index.php/2020/04/02/which-patients-are-in-greater-need-a-counterfactual-analysis-with-reflections-on-covid-19/)

2. *Start:* The original paper on causal bounds via response function variables is [Alexander Balke and Judea Pearl. Counterfactual probabilities: Computational methods, bounds and applications.](https://arxiv.org/abs/1302.6784)

    1. Another one is Bounds on Treatment Effects from Studies with Imperfect Compliance and should definitely be read if you are more deeper interest.

3. *A summary:* Wu et al. 2019 present a very nice exposition of causal bounds, via the application to fairness: [PC-Fairness: A Unified Framework for Measuring Causality-based Fairness](https://arxiv.org/abs/1910.12586)

4. *An alternative response function free formulation:* [Ronald Ramsahai Causal bounds and instruments](https://ora.ox.ac.uk/objects/uuid:e0c52783-3f19-4aa9-b101-5e22a4527e9d)
