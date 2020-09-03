Causal Inference Wiki
============================
*A friendly introduction to causal inference*

**DISCLAIMER: this is an alpha-version of this project. We hope to make it grow in quality and quantity as more people get involved. If interested, please reach out!**

![The ultimate question](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Chick-and-Egg.jpg)

This is meant to be a resource for causal-curious folks who are looking for accessible introduction to common topics in causal inference. 

* _We do not aim_ at replacing Wikipedia, or any of the [excellent textbooks](https://github.com/limorigu/causal-inf-handbook/blob/master/Suggested_Readings/Textbooks.md) already out there on the topic.

* _We do aim_ to include quick references to common topics of interest, and grow naturally with community's needs, expertise and interests. We hope to make this a collaborative project, so please get in touch if you'd like to make a contribution, or jump on it and create an issue or pull request.

Table of Contents
===============
1. **Common Terms (Terminology)**
    1. [_G-something terms_ (Overview)](Common_terms/G_something.md)
        1. G-estimation
        2. G-formula
        3. G-Identifiably
        4. G-etc.
    2. Interventions
    3. Counterfactuals
    <!---(Common_terms/Counterfactuals.md)--->
        
2. **Causal Discovery**
    
3. **Common Assumptions**
    1. Positivity
    <!---(Common_terms/Assumptions/Positivity.md)--->
    <!---Overlap--->
    2. SUTVA
    3. Consistency
    4. Compliance
    <!---(Common_terms/Assumptions/Compliance.md)--->
    5. [Exchangeability](Common_terms/Assumptions/exchangeability.ipynb)
        1. Ignorability (weak and strong)
        2. No-unmeasured confounding
4. **Types of Causal Effects**
     1. [ATE](Common_terms/Causal_Effects/ATE.md) 
     2. [CATE](Common_terms/Causal_Effects/CATE.md)
     <!---3. [HTE](Common_terms/Causal_Effects/CATE.md)--->
     4. [ITE](Common_terms/Causal_Effects/ITE.md)
     5. [Bounds on causal effects](Common_terms/Identifiability/CausalBounds.md)
5. **Potential Outcomes vs. Graphical Models**
     1. Other types of causality
         1. Granger causality, Causal Impact, etc.
6. **(Causal Effects) Identifiability**
     <!---1. What does it mean?
     2. How is it used differently?
     3. Does it always refer to causal parameters/claims or sometimes as well to “normal parameters”?--->
     1. Challenges to identifiability: sources of bias
        1. [Confounding](Common_terms/Identifiability/Confounding)
        2. (Sample) Selection Bias(Common_terms/Identifiability/Bias/Selection_bias.md)
     2. Common methods for identification
        1. Instrumental variables (IVs)
        <!---(Common_terms/Identifiability/IV.md)--->
        2. Diffs in Diffs
        3. Doubly robust methods
            1. 2 step regression/IV regression
            <!---(Common_terms/Identifiability/Doubly_Robust.md)--->
        2. Meta-learners
            1. S-learner
            3. T-learner
            3. R-learner
            4. X-learner 
        4. Negative controls
        5. Method of Moments (moment matching?)
        6. Propensity score and matching
        <!---(Common_terms/Identifiability/Propensity.md)--->
        7. Do-calculus
            1. [Backdoor criterion + adjustment](Common_terms/Identifiability/Do_calculus/Backdoor.md)
            2. [Frontdoor criterion + adjustment](Common_terms/Identifiability/Do_calculus/Frontdoor.md)
            3. [d-separation](Common_terms/Identifiability/Do_calculus/d-separation.md)
        8. Proxy variables
7. **Counterfactuals**
         
8. **Philosophy of Causality**
      1. Nancy Cartwright
         1. Hunting Causes
         2. Refer to Stanford Encyclopedia
      10. Inspiration
          1. http://marcfbellemare.com/wordpress/metrics-mondays
              1. e.g. http://marcfbellemare.com/wordpress/12869
          2. http://causality.cs.ucla.edu/blog/index.php/2014/11/09/causal-inference-without-graphs/
          
Community and Recommendations
===============
1. [**Suggested readings**]
    1. [_Textbooks_](https://github.com/limorigu/causal-inf-handbook/blob/master/Suggested_Readings/Textbooks.md)
    2. _Twitter/Blogs_
        
2. **Software**
    1. _Packages etc._
        1. [awesome-causalinference](https://github.com/tomron/awesome-causalinference)
        2. [Uber's Causal ML](https://github.com/uber/causalml)
    

# How to contribute

A general format for an entry is encouraged to have the following structure:
1. Motivation
2. Definition
3. Intuition (including examples and relation to other concepts)
4. Further reading

We aim for entries to provide a complete and concise introduction, with pointers to more elaborate sources.

# Credit
The Causal Inference Handbook is a joint effort by these [contributors](https://github.com/limorigu/causal-inf-handbook/graphs/contributors)

