---
layout: archive
title: "My research/What is BO?"
permalink: /bo/
author_profile: true
redirect_from:
  - /bo
---

What is the goal of BO?
======
Bayesian Optimisation (BO), as the name implies, is a method for _optimisation_, i.e. solving a problem of the following form:

$$ \max_{x \in \mathcal{X}} f(x) $$

where $\mathcal{X}$ is some set of "allowed" inputs to the function $f()$. However, contrary to standard optimisation techniques, BO can optimise function $f()$ without having to know anything about it! This problem setup is called _black-box optimisation_ and is very difficult, but at the same time, ubiquitous, as we will show below.

Why do we need BO?
======

It turns out that there are numerous tasks that can be framed as a _black-box optimisation_ problem. Examples include:
* Antibody design,  
* Logic circuit design, where $x$ is the sequence of operations on the circuit and $f()$  
*

As you can see, this kind of problem setup appears in multiple domains across engineering and medicine! So far, we only talked about the problems and not the solution, let us focus on that next.

How does BO work?
======
As we do not know the function formula, we are unable to analytically find an optimum of our function. At the same time, we are also unable to differentiate the function $f()$, which rules out the usage of gradient methods. What else can we try then?

In Bayesian Optimisation, we first look at the points, at which we have already evaluated the function. We use this knowledge to construct a _surrogate model_ of the function, as shown below:

<img src='/images/SampleBO1-1.png'>

Here, we have 5 points, based on which we construct a model of the function (solid line) and compute its uncertainty (shaded regions). In the example above, we have used a _surrogate model_ called  [Gaussian Process](https://en.wikipedia.org/wiki/Gaussian_process).

Given this model, we can now select the most promising point to try next! Usually, we want to try a point that has a large extrapolated value, but at the same time, we want to explore regions with high uncertainty to learn more about the function. A criterion that balances those two requirements is called an _acquisition function_. Given the model of the function $\mu()$ and its uncertainty $\sigma()$, a popular acquisition function called UCB, takes the form of 
$$\alpha(x) = \mu(x) + \beta \sigma(x)$$ where $\beta$ is the so-called _exploration bonus_, telling us how important it is for us to explore regions with high uncertainty.

More reading
====== 

