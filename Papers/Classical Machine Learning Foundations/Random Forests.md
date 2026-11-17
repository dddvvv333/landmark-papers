# Metadata
* Title: Random Forests
* Author: Leo Breiman.
* Published: 2001.
* Machine Learning, 45, 5-32, 2001.
# Random Forests
## Introduction
* Classification accuracy have increased from growing an ensemble of trees and letting them vote for the most popular class.
* In order to grow these, random vectors are generated that govern the growth of each tree.
* There have been different explorations, all of those procedures have in common is that for the kth three, a random vector is generated, independent of the past random vectors, but with the same distribution.
* And a tree is grown using the training set, resulting in a classifier.
* After a large number of trees is generated, they vote for the most popular class.
* This procedure is called **random forests**.
# Characterizing the accuracy of random forests
## Random forests converge
* As the number of trees increases, for almost surely all sequences converge.
## Strength and correlation
* The upper bound can be derived for the generalization error in terms of two parameters that are measures of how accurate the individual classifiers are and of the dependence between them.
* The c/s2 ratio is the correlation divided by the square of the strength, the smaller it is, the better.
# Using random features
* Some random forests reported in the literature have consistenly lower generalization error than others.
* To improve accuracy, the randomness injected has to minimize the correlation while maintaining strength.
* The forests studied here consist of using randomly selected inputs or combinations of inputs at each node to grow each tree.
* The resulting forests have accuracy that is comparable with Adaboost.
* This class of procedures has desirable characteristics:
	1. Its accuracy is as good as Adaboost and sometimes better.
	2. It's relatively robust to outliers and noise.
	3. It's faster than bagging or boosting.
	4. It gives useful internal estimates of error, strength, correlation and variable importance.
	5. It's simple and easily parallelized.
* Amit and Geman grew shallow trees for handwritten character recognition using random selection from a large number of geometrically defined features to define the split at each node.
* This is the starting point.
## Using out-of-bag estimates to monitor error, strength, and correlation
* In the experiments, bagging is used in tandem with random feature selection.
* Each new training set is drawn, with replacement, from the original training set.
* Then a tree is grown on the new training set using random feature selection.
* The trees grown are not pruned.
* Two reasons for using bagging:
	1. Use of bagging seems to enhance accuracy when random features are used.
	2. Bagging can be used to give ongoing estimates of the generalization error of the comibned ensemble of trees, as well as estimates for the strength and correlation.
* These estimates are done out-of-bag, which is explained as follows:
	* Assume a method for constructing a classifier from any training set.
	* Given a specific training set T, from bootstrap training sets $T_k$, construct classifiers and let these vote to form the bagged predictor.
	* For each y, x in the training set, aggregate the votes only over those classifiers for which $T_k$ does not containing y, x.
	* Call this the out-of-bag classifier.
	* Then, the out-of-bag estimate for the generalization error is the error rate of the out-of-bag classifier on the training set.
* Tibshirani and Wolpert and Macready, proposed using out-of-bag estimates as an ingredient in estimates of generalization error.
* The later ones worked on regression type problems and proposed a number of methods for estimating the generalization error of bagged predictors.
* Tibshirani used out-of-bag estimates of variance to estimate generalization error for arbitrary classifiers.
* The study of error estimates for bagged classifiers done by Braiman, gives empirical evidence tho show that those estimate is as accurate as using a test set of the same size as the training set.
* Therefore, using out-of-bag error estimate removes the need for a set aside test set.
* In each bootstrap training set, about one-third of the instances are left out.
* Therefore, these estimates are based on combining only about one-third as many classifiers as in the ongoing main combination.
* The error rate decreases as the number of combinations increases, the out-of-bag estimates will tend to overestimate the current error rate.
* To get unbiased estimates, it is necessary to run past the point where the test set error converges.
* Unlike cross-validation though, where bias is present but its extent is unnknown, the out-of-bag estimates are unbiaserd.
* Strength and correlation can also be estimated using out-of-bag methods.
* This gives internal estimates that are helpul in understanding classification accuracy and how to improve it.