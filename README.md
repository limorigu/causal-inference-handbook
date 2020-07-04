Causal Inference Handbook
============================
*A friendly introduction to causal inference*

<!-- # How to read
Head over to the [Wiki section](https://github.com/limorigu/causal-inf-handbook/wiki) for all entires on fundamentals of causal inference! -->

## Welcome to the causal inference handbook wiki!

This is meant to be a resource for causal-curious folks who are looking for accessible introduction to common topics in causal inference. 

![The ultimate question](https://github.com/limorigu/causal-inf-handbook/blob/master/img/Chick-and-Egg.jpg)

The Causal Dictionary
===============
1. **Common Terms (Terminology)**
    1. _G-something_
        1. G-estimation
        2. G-formula
        3. G-Identifiably
        4. G-etc.
        
2. **Causal Discovery versus Causal Effect Estimation**
    1. What do they do?
    
3. **Common Assumptions**
    1. [Positivity](Common_terms/Assumptions/Positivity.md)
        1. Overlap
    2. SUTVA
    3. Consistency
    4. [Compliance](Common_terms/Assumptions/Compliance.md)
    5. [Exchangeability](Common_terms/Assumptions/exchangeability.ipynb)
        1. Ignorability (weak and strong)
        2. No-unmeasured confounding
4. **Causal Effects**
     1. CATE
     2. HTE
     3. ITE
5. **Potential Outcomes vs. Graphical Models**
     1. Other types of causality
         1. Granger causality, Causal Impact, etc.
6. **Identifiability**
     1. What does it mean?
     2. How is it used differently?
     3. Does it always refer to causal parameters/claims or sometimes as well to “normal parameters”?
     4. Challenges to identifiability: sources of bias
        1. Confounding
        2. [(Sample) Selection Bias](Common_terms/Identifiability/Bias/Selection_bias.md)
     5. Common methods for identification
        1. [Instrumental variables (IVs)](Common_terms/Identifiability/IV.md)
        2. Diffs in Diffs
        3. Doubly robust methods
            1. [2 step regression/IV regression](Common_terms/Identifiability/Doubly_robust.md)
        4. Negative controls
        5. Method of Moments (moment matching?)
        6. [Propensity score and matching](Common_terms/Identifiability/Propensity.md)
        7. Do-calculus
            1. Backdoor criterion + adjustment
            2. Frontdoor criterion + adjustment
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
1. [**Jobs and Opportunities**](https://github.com/limorigu/causal-inf-handbook/blob/master/Jobs-and-Opportunities/Jobs-and-Opportunities.md)
    1. _Industry_
    2. _Academia_
        1. Quantum Causal Inference, see UAI mailer
        
2. **Software**
    1. _Packages etc._
    
3. **Suggested readings**
    1. _Textbooks_
    2. _Twitter/Blogs_
        1. https://github.com/tomron/awesome-causalinference



# How to contribute

To be determined, requires the repo to be public.
Suggested methods:
- pull requests
- raising issues
- adding contributors


# Credit
The Causal Inference Handbook is a joint effort by these [contributors](https://github.com/limorigu/causal-inf-handbook/graphs/contributors)


