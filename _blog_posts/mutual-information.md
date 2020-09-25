---
title: Mutual Information
layout: blog_post
include_math: true
citations: ["https://en.wikipedia.org/wiki/Joint_probability_distribution", "https://en.wikipedia.org/wiki/Mutual_information", "https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence"]
---
$$I(X;Y) = D_{KL}(P_{(X, Y)} \vert\vert\ P_X \cdot P_Y)$$
$$D_{KL}(P \vert\vert Q) = \sum_{x \in \mathcal{X}} P(x) \log \left( \frac{P(x)}{Q(x)}\right)$$

<p>If the variables are independent then $P_{(X, Y)} = P_X \cdot P_Y$. Thus the KL divergence will be zero so the mutual information will be zero.</p>
<p>On the other hand consider the other most extreme case, such that $P(X) = P(Y)$. </p>
<p>
Then this table represents $P(X, Y)$:
<table class="table">
  <thead>
    <tr>
      <th></th>
      <th>X=0</th>
      <th>X=1</th>
    </tr>
  </thead><br>
  <tbody>
    <tr>
      <td><b>Y=0</b></td>
      <td>.5</td>
      <td>0</td>
    </tr>
    <tr>
      <td><b>Y=1</b></td>
      <td>0</td>
      <td>.5</td>
    </tr>
  </tbody>
</table>
</p>
<p>
And this table represents $P_X \cdot P_Y$:
<table class="table">
  <thead>
    <tr>
      <th></th>
      <th>X=0</th>
      <th>X=1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Y=0</b></td>
      <td>.25</td>
      <td>.25</td>
    </tr>
    <tr>
      <td><b>Y=1</b></td>
      <td>.25</td>
      <td>.25</td>
    </tr>
  </tbody>
</table>
</p>
<p>
Then we only need to consider when the the joint distribution ($P_{(X, Y)}$) is not equal to zero. 
Thus we get $.5 \log \frac{.5}{.25} + .5 \log \frac{.5}{.25} = .5 \log 2 + .5 \log 2 = 1 $. So mutual information can sort of be thought of as how frequently the values of the two variables co-occur or how (in)dependent the two variables are.
</p>