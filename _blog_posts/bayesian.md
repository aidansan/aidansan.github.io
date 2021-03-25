---
title: Bayesian Learning
layout: blog_post
include_math: true
citations: ["Machine Learning a Probabilitistic Perspective: 2.2.2, 3.2"]
---
$$P(\theta \vert D) = \frac{P(\theta, D)}{P(D)} = \frac{P(D\vert \theta)P(\theta)}{\sum_{\theta'}P(D\vert \theta =\theta')P(\theta=\theta')}$$

Prior: $P(\theta)$. <br>
Likelihood: $P(D \vert \theta)$ <br>
Posterior: $P(\theta \vert D)$. <br>
Marginal: $P(D\vert \theta =\theta')P(D)$ <br>
Joint Distribution: $P(\theta, D)$
