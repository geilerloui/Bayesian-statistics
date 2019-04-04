## Bayesian Statistics: Techniques and Models

#### 1. Quizz Lesson 1

1.Which objective of statistical modeling is best illustrated by the following example?

You fit a linear regression of monthly stock values for your company. You use the estimates and recent stock history to calculate a forecast of the stock's value for the next three months.

o Quantify uncertainty	o Inference

o Hypothesis testing		o Prediction

1. Which objective of statistical modeling is best illustrated by the following example?

   A biologist proposes a treatment to decrease genetic variation in plant size. She conducts an experiment and asks you (the statistician) to analyze the data to conclude whether a 10% decrease in variation has occurred.

o Quantify uncertainty	o Inference

o Hypothesis testing		o Prediction

1. Which objective of statistical modeling is best illustrated by the following example?

   The same biologist form the previous question asks you how many experiments would be necessary to have a 95% chance at detecting a 10% decrease in plant variation.

o Quantify uncertainty	o Inference

o Hypothesis testing		o Prediction

1. Which of the following scenarios best illustrates the statistical modeling objective of inference?

- A venture capitalist uses data about several companies to build a model and makes recommendations about which company to invest in next based on growth forecasts.

- A natural language processing algorithm analyzes the first four words of a sentence and provides words to complete the sentence.

- A model inputs academic performance of 1000 students and predicts which student will be valedictorian after another year of school.

- A social scientist collects data and detects positive correlation between sleep deprivation and traffic accidents.

1. Which step in the statistical modeling cycle was **not** followed in the following scenario?

   Susan gathers data recording heights of children and fits a linear regression predicting height from age. To her surprise, the model does not predict well the heights for ages 14-17 (because the growth rate changes with age), both for children included in the original data as well as other children outside the model training data.  

   o Use the model		o Fit the model

   o Explore the data	o Plan and properly collect relevant data

1. Which of the following is a possible consequence of failure to plan and properly collect relevant data?

Your selected model will not be able to fit the data.

Your analysis may produce incomplete or misleading results.

You may not be able to visually explore the data.

You will not produce enough data to make conclusions with a sufficient degree of confidence.

1. For Questions 6 and 7, consider the following:

   Xie operates a bakery and wants to use a statistical model to determine how many loaves of bread he should bake each day in preparation for weekday lunch hours. He decides to fit a Poisson model to count the demand for bread. He selects two weeks which have typical business, and for those two weeks, counts how many loaves are sold during the lunch hour each day. He fits the model, which estimates that the daily demand averages 22.3 loaves.

   Over the next month, Xie bakes 23 loaves each day, but is disappointed to find that on most days he has excess bread and on a few days (usually Mondays), he runs out of loaves early.

   Which of the following steps of the modeling process did Xie skip?

Understand the problem

Postulate a model

Fit the model

Check the model and iterate

Use the model



1. What might you recommend Xie do next to fix this omission and improve his predictive performance?

Abandon his statistical modeling initiative.

Collect three more weeks of data from his bakery and other bakeries throughout the city. Re-fit the same model to the extra data and follow the results based on more data.

Plot daily demand and model predictions against the day of the week to check for patterns that may account for the extra variability. Fit and check a new model which accounts for this.

Trust the current model and continue to produce 23 loaves daily, since in the long-run average, his error is zero.

#### 2. Quizz Lesson 2

Q1:

Which of the following is one major difference between the frequentist and Bayesian approach to modeling data?

* Frequentist models require a guess of parameter values to initialize models while Bayesian models require initial distributions for the parameters.

* Frequentist models are deterministic (don't use probability) while Bayesian models are stochastic (based on probability).

* Frequentists treat the unknown parameters as fixed (constant) while Bayesians treat unknown parameters as random variables.

* The frequentist paradigm treats the data as fixed while the Bayesian paradigm considers data to be random.

Q2:

Suppose we have a statistical model with unknown parameter \thetaθ, and we assume a normal prior $\theta \sim \text{N}(\mu_0, \sigma_0^2)$, where $\mu_0$ is the prior mean and $\sigma_0^2$ is the prior variance. What does increasing $\sigma_0^2$ say about our prior beliefs about $\theta$?

* Increasing the variance of the prior **widens** the range of what we think $\theta$ might be, indicating **greater** confidence in our prior mean guess $\mu_0$.

* Increasing the variance of the prior **narrows** the range of what we think $\theta$might be, indicating **greater** confidence in our prior mean guess $\mu_0$.

* Increasing the variance of the prior **narrows** the range of what we think $\theta$might be, indicating **less** confidence in our prior mean guess $\mu_0$.

* Increasing the variance of the prior **widens** the range of what we think $\theta$ might be, indicating **less** confidence in our prior mean guess $\mu_0$.

Q3:

In the lesson, we presented Bayes' theorem for the case where parameters are continuous. What is the correct expression for the posterior distribution of \thetaθ if it is discrete (takes on only specific values)?

* $p(\theta \mid y) = \frac{ p(y \mid \theta) \cdot p(\theta) }{ \int p(y \mid \theta) \cdot p(\theta)\, d\theta }$

* $p(\theta_j \mid y) = \frac{ p(y \mid \theta_j) \cdot p(\theta_j) }{ \sum_j p(y \mid \theta_j) \cdot p(\theta_j) }$

* $p(\theta) = \int p(\theta \mid y) \cdot p(y) \, dy$

* $p(\theta) = \sum_j p(\theta \mid y_j) \cdot p(y_j)$

Q4:

For Questions 4 and 5, refer to the following scenario.

In the quiz for Lesson 1, we described Xie's model for predicting demand for bread at his bakery. During the lunch hour on a given day, the number of orders (the response variable) follows a Poisson distribution. All days have the same mean (expected number of orders). Xie is a Bayesian, so he selects a conjugate gamma prior for the mean with shape 33 and rate 1 / 151/15. He collects data on Monday through Friday for two weeks.

Which of the following hierarchical models represents this scenario?

* $$
  y_i|\lambda \sim Pois(\lambda)~~for,i=1,...,10 \\
  \lambda \sim Gamma(3,1/15)
  $$




* $$
  y_i|\lambda_i \sim Pois(\lambda_i)~~for,i=1,...,10 \\
  \lambda_i|\alpha \sim Gamma(\alpha,1/15) \\
  \alpha \sim Gamma(3.0,1.0)
  $$




* $$
  y_i|\lambda \sim Pois(\lambda)~~for,i=1,...,10 \\
  \lambda|\mu \sim Gamma(\mu,1/15) \\
  \mu \sim N(3.0,1.0^2)
  $$




* $$
  y_i|\mu \sim N(\mu, 1.0^2)~~for~i=1,...,10 \\
  \mu \sim N(3,15^2)
  $$


Q5

Which of the following graphical depictions represents the model from Xie's scenario?

a)

<img src="quizz2.1.png" height="200px">

b)

<img src="quizz2.2.png" height="150px">

c)

<img src="quizz2.3.png" height="150px">

d)

<img src="quizz2.4.png" height="150px">

Q6

  Graphical representations of models generally do not identify the distributions of the variables (nodes), but they do reveal the structure of dependence among the variables.

Identify which of the following hierarchical models is depicted in the graphical representation below.

<img src="quizz2.5.png" height="250px">

* $$
  y_i|\lambda \sim Pois(\lambda)~~for~i=1,...,10, \\
  \lambda \sim Gamma(3,1/15)
  $$




* $$
  y_i|\lambda_i \sim Pois(\lambda_i)~~for~i=1,...,10, \\
  \lambda_i|\alpha \sim Gamma(\alpha, 1/15) \\
  \alpha \sim Gamma(3.0,1.0)
  $$




* $$
  y_i | \lambda \sim Pois(\lambda) ~~for~i=1,...,10, \\
  \lambda | \mu \sim Gamma(\mu, 1/15) \\
  \mu \sim N(3,1.0^2)
  $$




* $$
  y_i | \mu \sim N(\mu, 1.0^2)~~for i=1,...,10, \\
  \mu \sim N(3,15^2)
  $$




Q7

Consider the following model for a binary outcome $y$:
$$
y_i|\theta_i \sim Bern(\theta_i),~~~i=1,...,6 \\
\theta_i|\alpha \sim Beta(\alpha, b_0), ~~~i=1,...,6 \\
\alpha \sim Exp(r_0)
$$
where $\theta_i$ is the probability of success on trial $i$. What is the expression for the joint distribution of all variables, written as $p(y_1, \ldots, y_6, \theta_1, \ldots, \theta_6, \alpha)$ and denoted by $p(\cdots)$? You may ignore the indicator functions specifying the valid ranges of the variables (although the expressions are technically incorrect without them).

**Hint:**

The PMF for a Bernoulli random variable is $f_y(y \mid \theta) = \theta^{y} (1-\theta)^{1-y}$ for $y=0$ or $y=1$ and $0 < \theta < 1$.

The PDF for a Beta random variable is $f_\theta( \theta \mid \alpha, \beta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \theta^{\alpha - 1} (1 - \theta)^{\beta - 1}$ where $\Gamma()$ is the gamma function, $0 < \theta < 1$ and $\alpha, \beta > 0$

The PDF for an exponential random variable is $f_\alpha( \alpha \mid \lambda) = \lambda \exp(-\lambda \alpha)$ for $\lambda, \alpha > 0$.

* $p(\cdots) = \prod_{i=1}^6 \left[ \theta_i^{y_i} (1-\theta_i)^{1-y_i} \frac{\Gamma(\alpha + b_0)}{\Gamma(\alpha) \Gamma(b_0)} \theta_i^{\alpha - 1} (1 - \theta_i)^{b_0 - 1} \right]$

* $p(\cdots) = \prod_{i=1}^6 \left[ \theta_i^{y_i} (1-\theta_i)^{1-y_i} \frac{\Gamma(\alpha + b_0)}{\Gamma(\alpha) \Gamma(b_0)} \theta_i^{\alpha - 1} (1 - \theta_i)^{b_0 - 1} \right] \cdot r_0 \exp(-r_0 \alpha)$

* $p(\cdots) = \prod_{i=1}^6 \left[ \theta_i^{y_i} (1-\theta_i)^{1-y_i} \right] \cdot \frac{\Gamma(\alpha + b_0)}{\Gamma(\alpha) \Gamma(b_0)} \theta^{\alpha - 1} (1 - \theta)^{b_0 - 1} \cdot r_0 \exp(-r_0 \alpha)$

* $p(\cdots) = \prod_{i=1}^6 \left[ \theta_i^{y_i} (1-\theta_i)^{1-y_i} \frac{\Gamma(\alpha + b_0)}{\Gamma(\alpha) \Gamma(b_0)} \theta_i^{\alpha - 1} (1 - \theta_i)^{b_0 - 1} r_0 \exp(-r_0 \alpha) \right]$

Q8

In a Bayesian model, let $y$ denote all the data and $\theta$ denote all the parameters. Which of the following statements about the relationship between the joint distribution of all variables $p(y, \theta) = p(\cdots)p(y,θ)=p(⋯) $and the posterior distribution $p(\theta \mid y)$ is true?

* They are proportional to each other so that $p(y, \theta) = c \cdot p(\theta \mid y)$ where cc is a constant number that doesn't involve $\theta$ at all.

* They are actually equal to each other so that $p(y, \theta) = p(\theta \mid y)$.

* The joint distribution $p(y,\theta)$ is equal to the posterior distribution times a function $f(\theta)$ which contains the modification (update) of the prior.

* Neither is sufficient alone--they are both necessary to make inferences about $\theta$.



#### 3. Quizz Lesson 3

Q1 

If a random variable $X$ follows a standard uniform distribution $(X \sim \text{Unif}(0,1))$, then the PDF of $X$ is $p(x) = 1p(x)=1$ for $0 \le x \le$ 1

We can use Monte Carlo simulation of $X$ to approximate the following integral: $\int_0^1 x^2 dx = \int_0^1 x^2 \cdot 1 dx = \int_0^1 x^2 \cdot p(x) dx = \text{E}(X^2)$

If we simulate 1000 independent samples from the standard uniform distribution and call them $x_i^*$ for $i=1,\ldots,1000$, which of the following calculations will approximate the integral above?

* $\frac{1}{1000} \sum_{i=1}^{1000}x_i^*$

* $\frac{1}{1000} \sum_{i=1}^{1000} {(x_i^* - \bar{x^*})}^2$ where $\bar{x^*}$is the calculated average of the $x_i^*$ samples.

* $\left( \frac{1}{1000} \sum_{i=1}^{1000} x_i^* \right)^2$

* $\frac{1}{1000} \sum_{i=1}^{1000} {x_i^*}^2$

Q2

Suppose we simulate 1000 samples from a $\text{Unif}(0, \pi)$ distribution (which has PDF $p(x) = \frac{1}{\pi}$ for $0 \le x \le \pi$ and call the samples $x_i^*$ for $i = 1, \ldots, 1000$.

If we use these samples to calculate $\frac{1}{1000} \sum_{i=1}^{1000} \sin( x_i^* )$, what integral are we approximating?

* $\int_{-\infty}^\infty \sin( x ) dx$

* $\int_0^\pi \frac{ \sin( x ) }{ \pi } dx$

* $\int_0^1 \frac{ \sin( x ) }{ \pi } dx$

* $\int_0^1 \sin( x ) dx$

Q3

Suppose random variables $X$ and $Y$ have a joint probability distribution $p(X, Y)$. Suppose we simulate 1000 samples from this distribution, which gives us 1000 $(x_i^*, y_i^*)$pairs.

If we count how many of these pairs satisfy the condition $x_i^* < y_i^*$ and divide the result by 1000, what quantity are we approximating via Monte Carlo simulation?

* $\text{Pr}[ X < Y]$

* $\text{Pr}[ X < \text{E}(Y) ]$

* $\text{Pr}[ \text{E}(X) < \text{E}(Y) ]$

* $\text{E}( XY)$

Q4

If we simulate 100 samples from a $\text{Gamma} (2, 1)$ distribution, what is the approximate distribution of the sample average $\bar{x^*} = \frac{1}{100} \sum_{i=1}^{100} x_i^*$?

**Hint**: the mean and variance of a $\text{Gamma}(a,b)$ random variable are $a/b$ and $a/b^2$ respectively.

* $\text{Gamma}(2, 0.01)$

* $\text{N}(2, 2)$

* $\text{N}(2, 0.02)$

* $\text{Gamma}(2, 1)$

Q5

For Questions 5 and 6, consider the following scenario:

Laura keeps record of her loan applications and performs a Bayesian analysis of her success rate $\theta$. Her analysis yields a $\text{Beta}(5,3)$ posterior distribution for $\theta$.

The posterior mean for $\theta$ is equal to $\frac{5}{5+3} = 0.6255+35=0.625$. However, Laura likes to think in terms of the odds of succeeding, defined as $\frac{\theta}{1 - \theta}$, the probability of success divided by the probability of failure.

Use R to simulate a large number of samples (more than 10,000) from the posterior distribution for $\theta$ and use these samples to approximate the posterior mean for Laura's odds of success ( $\text{E}(\frac{\theta}{1-\theta})$.

Report your answer to at least one decimal place.

* Enter answer here

Q6

Laura also wants to know the posterior probability that her odds of success on loan applications is greater than 1.0 (in other words, better than 50:50 odds).

Use your Monte Carlo sample from the distribution of \thetaθ to approximate the probability that $\frac{\theta}{1-\theta}$ is greater than 1.0.

Report your answer to at least two decimal places.

* Enter answer here

Q7

Use a (large) Monte Carlo sample to approximate the 0.3 quantile of the standard normal distribution ($\text{N}(0,1)$), the number such that the probability of being less than it is 0.3.

Use the $\tt quantile$ function in R. You can of course check your answer using the $\tt qnorm$ function.

Report your answer to at least two decimal places.

* Enter answer here

Q8

To measure how accurate our Monte Carlo approximations are, we can use the central limit theorem. If the number of samples drawn mm is large, then the Monte Carlo sample mean $\bar{\theta^*}$ used to estimate $\text{E}(\theta)$ approximately follows a normal distribution with mean $\text{E}(\theta)$ and variance $\text{Var}(\theta) / m$. If we substitute the sample variance for $\text{Var}(\theta)$, we can get a rough estimate of our Monte Carlo standard error (or standard deviation).

Suppose we have 100 samples from our posterior distribution for $\theta$, called $\theta_i^*$, and that the sample variance of these draws is 5.2. A rough estimate of our Monte Carlo standard error would then be $\sqrt{ 5.2 / 100 } \approx 0.2285.2/100≈0.228$. So our estimate $\bar{\theta^*}$ is probably within about $0.4560$ (two standard errors) of the true $\text{E}(\theta)$

What does the standard error of our Monte Carlo estimate become if we increase our sample size to 5,000? Assume that the sample variance of the draws is still 5.2.

Report your answer to at least three decimal places.

* Enter answer here













