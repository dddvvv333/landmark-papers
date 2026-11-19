# Metadata
* Title: A Decision-Theoretic Generalization of On-Line Learning and an Application to Boosting
* Authors: Yoav Freund and Robert E. Schapire
* December 19, 1996.
* AT&T Labs.
# Introduction
* The paper introduces a simple algorithm for solving dynamic allocation problems.
* But also, for a lot of learning problems.
* It also derives in a new algorithm for "boosting".
	* Converting a "weak" PAC learning algorithm that performs just sligthly better than random guessing into one with arbitrarily high accuracy.
* Formalization of the *on-line allocation model*:
	* The allocation agent A has N options or *strategies* to choose from.
	* Those are numbered using the integers from $1$ to $N$.
	* At each time step $t$ the allocator $A$ decides on a distribution $p'$ over the strategies.
	* Each strategy $i$ then suffer some *loss*, which is determined by the (possibly adversarial) "enviroment".
	* The loss suffered by $A$ is then the average loss of the strategies with respect to $A$'s chosen allocation rule.
	* This function is called *mixture loss*.
* In this paper, the authors assume that the loss is bounded by any strategy, so without loss of generality, the loss value is between $0$ and $1$.
* The goal of the algorithm $A$ is to minimize its cumulative loss relative to the loss suffered by the best strategy.
## Boosting
* "rule-of-thumb", very rough and inaccurate, but canb provide predictions that are at least a little bit better than random guessing.
* In different scenarios, different rules-of-thumb.
* To use those in maximumg advantage, is neccesary to curate the scenarios and combine them efficiently (the rof).
* *Boosting* refers to this, a accurate prediction rule combined rough and moderatly innacurate rules-of-thumb.
* The formalizations is the following:
	* The booster is provided with a set of labelled training examples.
	* On each round, the booster devises a distribution over the set of examples, and requests a *weak hypothesis* with low error with respect to the distribution.
	* The distribution specifies the relative importance of each example for the current round.
	* After some rounds, the booster must combine the weak hypotheses into a single prediction rule.
	* Unlike previous boosting algorithms, this new one needs o prior knowledge of the accuracies of the weak hypotheses.
	* It adapts to these accuracies and generates a weighted majority hypothesis in which the weight of each weak hypothesis is a function of its accuracy.
* The bound on the accuracy of the final hypothesis impreoves when any of the weak hypotheses is improved when any of the weak hypotheses is improved.
* If all the weak hypotheses all have the same accuracy, the performance of the nwe algorithm is very close to that achieved by the best of the known boosting algorithms.
# The on-line allocation algorithm and its analyisis
* The algorithm is called **Hedge**.
* Pseudo code:
```code
Algorithm Hedge(Beta)
Parameters Beta in [0, 1]
	initial weight vector w in [0, 1] with the sum (W) of them equal to 1 
	number of trials T
Do for t = 1, ..., T
	1. Choose allocation
	   p_t = w_t / W
	2. Receive loss vector l_t in [0, 1] from enviroment
	3. Suffer loss p_t * l_t
	4. Set the new weights vector to be w_t * Beta ** l_t
```
## Analysis
* The main idea is to derive upper and lower bounds 