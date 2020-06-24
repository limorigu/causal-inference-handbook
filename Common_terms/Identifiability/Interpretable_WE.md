Interpretable words embeddings -- what has been done
=========

**_Word2Sense, 2019_**
~**Summary**~
* The central contender in this space seems to be Word2Sense, which was pusblished in August 2019 at the annual ACL. At the core, it is an LDA-based generative model, which leads to interpretable representation for words: where each dimension of the embedding space is corresponds to a fine-grained *sense* and the non-negative value of the embedding along the j-th dimension represents the relevance of the j-th sense to the word. 

* The current standard is that the numerical values of a WE are meaningful in relation to representations of other words. The aim of Word2Sense is instead to "design an interpretable embedding whose cooredinates have a clear meaning to humans".

* Words are represented as probability distributions over senses so that the magnitude of each coordinate represents the relative importance of the corresponding sense to the word.

* The method consists of a generative model for the co-occurance matrix: (1) associate w/ each word w, a sense distribution \theta_w w\ dirichlet prior; (2) form a context around a target word w, by sampling sense z according to \theta_w, and sample words from the distribution of sense z. (allows to use fast-inference tools such as WarpLDA to recover few thousand fine-grained senses from large corpora). The resulting Word2Sense vectors are sparse and high dimensional (in the thousands), with number of non-zeros up to 100. 

* The resulting vectors are claimed to outperform probabilistic embeddings (Athiwarkarkun and Wilson, 2017) at tasks such as word entailment, and complete with word2vec embeddings and multi-prototype embeddings in similarity and relatendness tasks. 

~**Method**~
* V is the vector of unique tokens in corpus. C is a co-occurance matrix within a context window n. 

* The algorithm has the following components:
	1. LDA to infer *sense* model \beta.
	2. use \beta to encode a word w as a k'-dimensional \miu-sparse vector \theta_w. 
	3. \alpha and \gamma are Dirichlet priors of \theta_w (the sense distr. of w)
	4. JS is a k x k matrix that measures the sim. b/w senses (with Jensen Shannon divergence)

* Algorithm to recover senses:
	1. For each word w, generate a distribution over senses \theta_w from the Dirichlet distribution with prior \alpha. 
	2. For each context c_w around the target word w, and for each of the 2n tokens in c_w, 
		1. sample sense z ~ Multinominal(\theta_w)
		2. sample token c ~ Multinomial(\beta_{z_n})

* Putting it togehter, Given a Dirichlet prior of parameter \alpha on sense distribution of C_w and \beta, the distribution over context words for each sense, document C_w (and thus C) can be generated as follows:
	1. Generate \theta_w ~ Dirichlet(\alpha)
	2. Repeat N times to generate C_w:
		1. z ~ Mutlinomial(\theta_w)
		2. c ~ Multinomial(\beta_z)



**_SPINE: SParse Interpretable Neural Embeddings_**



