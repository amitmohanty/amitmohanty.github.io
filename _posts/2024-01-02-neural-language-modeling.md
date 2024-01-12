---
layout: post
title: Neural Language Modeling
date: 2024-01-02 04:19 -0800
math: true
---

We will first consider some basic statistical modeling of a high dimensional distributed data. The _joint probability_ of a set of random variables $$ z_1,~z_2,\cdots, ~z_n $$ can be modeled as the product of conditional probabilities as follows:
$$
\hat{P}(z_1, z_2, \cdots, z_n) = \prod_{i} \hat{P}\Big(z_i \Big| g_i(z_{i-1},~z_{i-2},~\cdots, z_1)\Big)
$$

where $$ g_i(\cdot) $$ is a function represented by a neural network with special left-to-right structure.

# Language Modeling
At a very basic level, language models assign a probability to a piece of text (words, phrases, sentences). More technically, the goal is as follows:

> __Goal__: Compute the probability $$ \mathbb{P}(w_{1:n}) = \mathbb{P} (w_1, w_2, \cdots, w_n) $$ of a sequence of words $$ w_{i:n} = (w_1, w_2, \cdots, w_n) $$.

Using __chain rule of probability__, we can express $$\mathbb{P}(w_{1:n}) $$ as follows:

$$
\begin{equation}
\mathbb{P}\Big(w_{1:n}\Big) = \mathbb{P}\Big(w_1\Big)~\mathbb{P}\Big(w_2|w_1\Big)~\mathbb{P}\Big(w_3|w_{1:2}\Big)~\mathbb{P}\Big(w_4|w_{1:3}\Big)~\cdots~\mathbb{P}\Big(w_n|w_{1:(n-1)}\Big) = \prod\limits_{k=1}^n \mathbb{P}\Big(w_k|w_{1:(k-1)}\Big) \label{eq:chain_rule}
\end{equation}
$$

<!-- Eq. e\eqref{eq:chain_rule} -->
Above equation shows the connection between computing the joint probability of a sequence and computing the conditional probability of a given word given previous words.

Using Bayes' Theorem, we can express $$\mathbb{P}(w_{1:n}) =  $$

## Evaluation
### Perplexity
Before we do the evaluation of the model, we need to define a metric to evaluate it on. A commonly used metrics for this purpose is __perplexity__.
> **Definition**: The perplexity $$\mathbf{Perp}(\mathcal{T}\vert \mathcal{L})$$ of a language model $$\mathcal{L}$$ on a test set is the inverse of probability of the test set word sequence $$ \mathcal{T} = wt_{1:N} = (wt_1,~wt_2, \cdots, wt_N)$$.

Mathematically, we can write and simplify using _chain rule of probability_:

$$ 
\begin{align} 
\mathbf{Perp}(\mathcal{T}\vert \mathcal{L}) &  = \sqrt[
N]{\frac{1}{\mathbb{P}(wt_{1:N})}}\\ & = \sqrt[
N]{\frac{1}{\mathbb{P}(wt_1~wt_2~\cdots~wt_N)}}\\ & = \sqrt[
N]{\prod\limits_{i = 1}^N\frac{1}{\mathbb{P}(wt_i\vert wt_1~wt_2\cdots~wt_{i-1})}}
\end{align} 
$$

For a _n-gram model_ ($$ n \ge 2$$), this simplifies to:

$$ 
\begin{align} 
\mathbf{Perp}(\mathcal{T}\vert \mathcal{L}) & = \sqrt[N]{\prod\limits_{i=1}^N\frac{1}{\mathbb{P}(wt_{i}\vert wt_{i-n+1}~wt_{i-n+2}~\cdots~ wt_{i-1})}} 
\end{align} 
$$

For a _bigram_ and _trigram_ models, this simplifies to the the followings, respectively:



For a _unigram model_, this simplifies to:

$$ 
\begin{align} 
\mathbf{Perp}(\mathcal{T}\vert \mathcal{L}) &  = \sqrt[\displaystyle
n]{\prod\limits_{i=1}^n\frac{1}{\mathbb{P}(wt_{i})}} 
\end{align} 
$$

The higher the conditional probabilities, the lower the _perplexity score_. Therefore, minimizing perplexity is equivalent to maximizing the conditional probability according to the language model of choice. 














Statistical language model is about \$$ w_1^L$$

$$
w_1^L = \{w_1, w_2, \cdots, w_n\}
$$

<!-- Inline math in lines, NO blank lines -->

"Lorem ipsum dolor sit amet, $$ LaTeX_math_expression $$ consectetur adipiscing elit."

<!-- Inline math in lists, escape the first `$` -->

1. \$$ LaTeX_math_expression $$
2. \$$ LaTeX_math_expression $$
3. \$$ LaTeX_math_expression $$
