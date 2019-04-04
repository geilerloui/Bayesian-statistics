# Bayesian Statistics

This repository contains material related to Coursera's [Bayesian Statistics: From Concept to Data Analysis](), [Bayesian Statistics: Techniques and Models]() and [Bayesian Methods for Machine Learning]()

## Table Of Contents

### 1. Bayesian Statistics: From Concept to Data Analysis

* [Probability and Bayes Theorem]() In this module, we review the basics of probability and Bayes Theorem. In Lesson 1, we introduce the different paradigms or definitions of probability and discuss why. Probability provides a coherent framework for dealing with uncertainty. In Lesson 2, we review the rules of conditional probability and introduce Bayes theorem. Lesson 3 review common probability distribution for discrete and continuous random variables
* [Statistical Inference]() This module introduces concepts of statistical inference from both frequentist and Bayesian perspectives. Lesson 4 takes the frequentist view, demonstrating maximum likelihood estimation and confidence intervals for binomial data. Lesson 5 introduces the fundamentals of Bayesian inference. Beginning with a binomial likelihood and prior probabilities for simple hypotheses, you will learn how to use Bayes’ theorem to update the prior with data to obtain posterior probabilities. This framework is extended with the continuous version of Bayes theorem to estimate continuous model parameters, and calculate posterior probabilities and credible intervals. 
* [Priors and Models for Discrete Data]() In this module, you will learn methods for selecting prior distributions and building models for discrete data. Lesson 6 introduces prior selection and predictive distributions as a means of evaluating priors. Lesson 7 demonstrates Bayesian analysis of Bernoulli data and introduces the computationally convenient concept of conjugate priors. Lesson 8 builds a conjugate model for Poisson data and discusses strategies for selection of prior hyperparameters. 
* [Models for Contunous Data]() This module covers conjugate and objective Bayesian analysis for continuous data. Lesson 9 presents the conjugate model for exponentially distributed data. Lesson 10 discusses models for normally distributed data, which play a central role in statistics. In Lesson 11, we return to prior selection and discuss ‘objective’ or ‘non-informative’ priors. Lesson 12 presents Bayesian linear regression with non-informative priors, which yield results comparable to those of classical regression. 

### 2. Bayesian Statistics: Techniques and Models

- [Lesson 1: Statistical modelling and Monte Carlo estimation]() Statistical modeling, Bayesian modeling, Monte Carlo estimation
- [Markov chain Monte Carlo (MCMC)]() Metropolis-Hastings, Gibbs sampling, assessing convergence
- [Common statistical models]() Linear regression, ANOVA, logistic regression, multiple factor ANOVA
- [Count data and hierarchical modelling]() Poisson regression, hierarchical modeling
- [Project: XXX]() Peer-reviewed data analysis project

### 3. Bayesian Methods for Machine Learning

* [Lesson 1: Introduction to Bayesian methods & Conjugate priors]() Welcome to first week of our course! today we will discuss what bayesian methods are and what are probabilistic models. We will see how they can be used to model real-life situations and how to make conclusions from them. We will also learn about conjugate priors — a class of models where all math becomes really simple.
* [Lesson 2: Expectation-Maximization algorithm]() This week we will about the central topic in probabilistic modeling: the Latent Variable Models and how to train them, namely the Expectation Maximization algorithm. We will see models for clustering and dimensionality reduction where Expectation Maximization algorithm can be applied as is. In the following weeks, we will spend weeks 3, 4, and 5 discussing numerous extensions to this algorithm to make it work for more complicated models and scale to large datasets. 
* [Variational Inference & Latent Dirichlet Allocation]() This week we will move on to approximate inference methods. We will see why we care about approximating distributions and see variational inference — one of the most powerful methods for this task. We will also see mean-field approximation in details. And apply it to text-mining algorithm called Latent Dirichlet Allocation
* [Markov Chain Monte-Carlo (MCMC)]() This week we will learn how to approximate training and inference with sampling and how to sample from complicated distributions. This will allow us to build simple method to deal with LDA and with Bayesian Neural Networks — Neural Networks which weights are random variables themselves and instead of training (finding the best value for the weights) we will sample from the posterior distributions on weights.
* [Variational Autoencoder]() Welcome to the fifth week of the course! This week we will combine many ideas from the previous weeks and add some new to build Variational Autoencoder -- a model that can learn a distribution over structured data (like photographs or molecules) and then sample new data points from the learned distribution, hallucinating new photographs of non-existing people. We will also the same techniques to Bayesian Neural Networks and will see how this can greatly compress the weights of the network without reducing the accuracy.
* [Gaussian processes & Bayesian optimization]() Welcome to the final week of our course! This time we will see nonparametric Bayesian methods. Specifically, we will learn about Gaussian processes and their application to Bayesian optimization that allows one to perform optimization for scenarios in which each function evaluation is very expensive: oil probe, drug discovery and neural network architecture tuning. 
* [Final project]() In this module you will apply methods that you learned in this course to this final project

## Bibliography

* [The Deep Learning Textbook](http://www.deeplearningbook.org/), from Ian GoodFellow ...

