Probability, that given an assignment of treatment to individuals Z, they will actually receive or take the treatment, D. In randomized control trials, compliance is usually believed to be quite high due to close monitoring of the process, but often more of an issue in other settings.

* Randomisation implies that the treatment assignment Z is independent of all the pre-assignment variables (including the potential outcomes) thus unconfoundedness holds  
* However, in case of non-compliance the actual treatment D is not always the same as the assigned treatment Z and it is a post-assignment variables: conditioning on D is harmful since it violates the unconfoundedness assumption

There are estimates that take non-compliance into account, including 
Intention to Treat (ITT): 
* ITT = E[Y(1,D(1)) - Y(0, D(0))]
* Complier Average Causal Effect (CACE), AKA ITT for compliers
* Local Average Treatment Effect (LATE)

For more see https://www.bristol.ac.uk/media-library/sites/cmm/migrated/documents/ci-non-compliance.pdf