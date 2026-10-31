---
title: KV Caching
layout: blog_post
include_math: true
citations: ["Attention Is All You Need: 3.2.3", "Hugging Face Blog, KV Caching: https://huggingface.co/blog/not-lain/kv-caching"]
---
**Standard Attention Process**

1. You start with the previous layer outputs: $X$
2. You down-project / matrix multiply by weight matrices, $W^Q, W^K, W^V \in \mathbb{R}^{512 \times 64}$ (8 heads).
3. You compute attention $= \text{softmax}\left(\frac{QK^T}{\sqrt{64}}\right)V$
    1. Additionally a mask is applied - "We implement this inside of scaled dot-product attention by masking out (setting to $-\infty$) all values in the input of the softmax which correspond to illegal connections."

Let's say we're generating a string with 4 tokens

`<bos> I like pizza`

**First decoding step:** We condition the model on `<bos>` <br>
At every layer of the model the representation is built from one single Query and Key and Value (representing `<bos>` itself)

$$\text{softmax}\left(\frac{q_{\text{bos}} \cdot k_{\text{bos}}}{\sqrt{64}}\right) v_{\text{bos}} = 1 \cdot v_{\text{bos}} = v_{\text{bos}}$$

**Second decoding step:** The model is now conditioned on `<bos>` and "I" <br>
Due to the causal mask, the BOS representation is still only composed from the single query and key, and value representing `<bos>`, but now the "I" representation is based on

$$(q_{\text{I}} \cdot k_{\text{bos}})\, v_{\text{bos}} + (q_{\text{I}} \cdot k_{\text{I}})\, v_{\text{I}}$$

(note we are ignoring the softmax & scaling here)

**Third decoding step:** The model is now conditioned on `<bos>`, "I" and "like" <br>
The BOS representation is based on the single query and key, and value (not affected by I or like's rep) <br>
The I representation is based only on I and `<bos>` representations, but now the "like" representation is

$$(q_{\text{like}} \cdot k_{\text{bos}})\, v_{\text{bos}} + (q_{\text{like}} \cdot k_{\text{I}})\, v_{\text{I}} + (q_{\text{like}} \cdot k_{\text{like}})\, v_{\text{like}}$$

(note we are ignoring the softmax & scaling here)

**Why is the Query not cached?**

The query vector is only needed to compute the representation for a particular token. Since we already have the key and value vectors (since they're cached) the earlier query vectors are not needed in later steps.

**When a new input token is added why don't the input vectors change?**

Because of the causal mask. In attention, each token representation is only based on the previous tokens and itself. All other parts of the transformer (e.g. feedforwards, skip connections) operate on each token representation independently.

(Typeset with Claude)
