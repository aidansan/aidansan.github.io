---
title: Entropy
layout: blog_post
include_math: true
citations: ["https://en.wikipedia.org/wiki/Entropy_(information_theory)", "https://en.wikipedia.org/wiki/Bernoulli_distribution"]
---
<p>Entropy is generally thought of as disorder. The formula for entropy is given by: $H(X) = - \sum_{i=1}^{n}P(x_i)\log P(x_i)$. 
  If we consider $X = \text{Bernoulli}(p)$, we can clearly see that entropy is highest when we cannot easily guess what value the random variable will take (when $p=.5$).
  Entropy is lowest at 0 when we know the value that $X$ will always take ($p = 0$ or $p=.5$).
</p>
<iframe src="https://www.desmos.com/calculator/0f9brhjk3v?embed" width="500px" height="500px" style="border: 1px solid #ccc" frameborder=0></iframe>
