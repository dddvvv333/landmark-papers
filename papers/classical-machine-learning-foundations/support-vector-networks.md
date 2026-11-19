# Metadata
* Title: Support-Vector Networks
* Authors: Corinna Cortes & Vladimir Vapnik
* Published in 1995.
* Machine Learning, 20, 273-297.
# Content
## Introduction
* Points to R.A. Fisher for suggesting the first algorithm for pattern recognition.
* Points to Rosenblat for exploring a different kind of learning machines: Perceptrons or Neural Networks ([[the-perceptron-a-probabilistic-model-for-information-storage-and-organization-in-the-brain]]).
* Points to the fact that there exists and algorithm to minimize the error on a set of vectors belonging to a pattern recognition problem, the back propagation algorithm ([[learning-representations-by-back-propagating-errors]]).
* The article proposes a new type of learning machine, the suport-vector network.
* The support-vector network implementes the following idea: it maps the input vectors into some high dimensional feature space $Z$ through some non-linear mapping chosen a priori.
* Two problems arise from this approach:
	1. Conceptual: How to find a separating [[hyperplane]] that will generalize well, the [[dimensionality]] of the [[feature-space|feature-space]] will be huge.
	2. Technical: How computationally to treat such high-dimensional spaces.
* The conceptual part of this problem was solved in 1965 for the case of *optimal hyperplanes* for separable classes. 
	* An optimal [[hyperplane]] is here defined as the [[linear-decision-function|linear decision function]] with maximal margin between the vectors of the two classes.
	* It was observed that to construct such optimal [[hyperplane|hyperplane]] one only has to take into account a small amount of the training data, the so called *support vectors*, which determine this margin.
* The technical problem is solved by changing the order of operations for constructing a decision function, meaning, we can first compare two vectors in input space and then make a [[non-linear-transformation|non-linear transformation]] of the value of the result.
* The technique of support-vector networks was first developed for the restricted case of separating training data without errors.
	* This article extend the approach of support vector networks to cover when separation without error on the training vectors is impossible.
	* With that, the support-vector networks can be considered a new class of [[learning-machine|learning machine]], as powerful and universal as [[neural-networks|neural networks]]ks (in words of the authors).
## Optimal Hyperplanes
### The Optimal Hyperplane Algorithm
* The optimal [[hyperplane]] is the unique one which separates the training data with a maximal margin.
* If the training set cannot be separated by a [[hyperplane]], the margin bteween patterns of the two classes becomes arbitrary small, resulting in the value of the functional $W(\Lambda)$ turning arbitrary large.
* Maximizing the functional one therefore eithre reaches a maximum or one finds that the maximum exceeds some given constant.
## The Soft Margin Hyperplane
* When the training data cannot be separated without eror, we want to separate it with a minimal number of errors.
* If we exclude the subset of training errors from the training set, one can separate the remaining part of the training set without errors.
* To separate the remaining part of the training data one can construct an optimal separating [[hyperplane]].
* Note that the problem of constructing a [[hyperplane]] which minimizes the number of errors on the training set is in general NP-complete. To avoid that, the authors simplify the problem.
## The Method of Convolution of the Dot-Product in Feature Space
* The previous sections were refering to [[hyperplane|hyperplanes]] in the input space.
* To construct one in a [[feature-space|feature space]], one first has to transform the n-dimensional input vector x into an N-dimensional feature vector through a choice of an N-dimensional vector function.
## General Features of Support-Vector Networks
### Constructing the Decision Rules by Support-Vector Networks is Efficient
* The solution to the optimization problem can be found efficiently by solving intermediate optimization problems determined by the training data, that currently constitute the support vectors.
### The Support-Vector Network is a Universal Machine
* They are a general class of learning machines which changes its set of decision functions simply by changing the form of the dot-product.
### Support-Vector Networks and Control of Generalization Ability
* To control the generalization ability of a learning machine, one has to control two different factors, the error-rate on the training data and the capacity of the learning machine as measured by its VC-dimension.
## Conclusions
* The support-vector network is a new learning machine for two-group classification problems.
* It combines 3 ideas:
	1. The solution technique from optimal [[hyperplane|hyperplanes]].
	2. The idea of [[convolution]] of the [[dot-product]].
	3. The notion of [[soft-margins|soft margins]].
* The [[algorithm]] has been tested and compared to the performance of other classical algorithms.
* Despite the simplicity, this new algorithm exhibits a very fine performance in the comparison study.
# Notes
* Many of the solutions and implementations use very simplified approachs and values, they are consistent with that and with the idea that this simplified approach does not perjudicate the results and performance of the [[learning-machine|learning machine]].
* This is only for two groups, meaning, [[binary-classification|binary classification]].
