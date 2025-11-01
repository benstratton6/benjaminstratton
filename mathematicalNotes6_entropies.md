---
title: Entropies  
subject: 
# subtitle: The space in which quantum states live
# short_title: How to MyST
authors:
  - name: Benjamin Stratton
    # affiliations:
    #   - Executable Books
    #   - Curvenote
    orcid: 0009-0001-2746-3668
    email: ben.stratton@bristol.ac.uk
# license: CC-BY-4.0
keywords: Entropy, Relative Entropy, Rényi Entropies. 
abstract: Some details about classical and quantum entropy functions
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(Entropy_target)=
Broadly, entropy functions describe the level of uncertainty in a probability distribution. Here, we detail the underlying concepts that leads to the construction of entropy functions. 

## Information gain or Surprisal

Consider a discrete random variable $X$, where the one gets the outcome $x$ with probability $p_x$. If there are $n$ possible outcomes, this can be described by the probability distribution 
\begin{equation}
\bm{p}=(p_1, p_2, p_3, \ldots, p_n) ~ ~ : ~ ~ p_x \geq 0~\forall~x, ~ ~\sum_{x=1}^n p_x=1.
\end{equation}
If one looks at the outcome of the random variable and sees that it is $y$, then the information they have gained from now knowing this is defined by
\begin{equation}
    I(p_y) \coloneqq -\log(p_y).
\end{equation}
It can be seen that if the outcome $y$ occurs with high probability, then $I(p_y)$ is very small; if the outcome $y$ occurs with low probability, then $I(p_y)$ is very large. That is, we gain lots of information if we are surprised about the outcome i.e., that event had a low probability of occurring. For this reason, the function $I(\cdot)$ is sometimes refereed to as the **surprisal**.  

:::{dropdown} Mathematical Justifications for $I(\cdot)$

The mathematical justifications for $I(\cdot)$ being the correct function for quantify the information gain is: 
1. **The information gain should depend only on the probability of a given outcome occurring, not on its label.** 
    - Given a probability distribution $\bm{p} = (0.75,0.25)$ it should not matter if this gives the outcomes of a coin or the color of ball, the theory of the information gain should be independent of the physical system in which that information is encoded. 
2. **The function should be a smooth function of probability.**
    - This means there are no jumps in the function and it varies continuously from max information gain to minimum information gain.  
3. $\bm{I(p_yp_z) = I(p_y) + I(p_z)}$ 
    - The probability of two independent events $y$ and $z$ occurring is $p_yp_z$. This condition then means that the information gained from the two independent events occurring is the sum of the information gained from the individual events. This can be justified physically, as if the events are independent then learning about one should not tell us about the other. 

:::

```{figure} mathematicalNotes_entropy_suprisal.png
:alt: 
:class: bg-primary
:width: 600px
:align: center
:target: convexity_figure_graph_target

The probability distribution of getting each outcome of a random variable as compared to the information gain of getting each outcome (the surprisal). 
```

## Entropies

The Shannon entropy of the random variable $X$ is then nothing more then the average information gain:
\begin{equation}
    \begin{split}
            H(X) \coloneqq  \mathbb{E}_{\bm{p}} \big[ I(p_x) \big] &=  -\sum_{x=1}^n p_x \log(p_x), \\
    \end{split}
\end{equation}
where $\mathbb{E}_{\bm{p}} \big[ \cdot \big]$ is the expectation value of $(\cdot)$ over the probability distribution $\bm{p}$. 

The entropy can be thought of as either: 
 - a measure of the uncertainty in the outcome of the random variable before the outcome is known
 - a measure of how much information is gained after the outcome of a random variable becomes known. 

:::{dropdown} Example

Let the random variable $X$ have a probability distribution 
\begin{equation}
\bm{p} = (0.7,0.2,0.1).
\end{equation}

The information gain or surprisal is then  
\begin{equation}
- \log_2\big(\bm{p}\big) = (0.51,2.32,3.32),
\end{equation}
where we have chosen to use log based two. 

The entropy is then 
\begin{align*}
H(X_{\bm{p}}) &= (0.7 \times 0.51) + (0.2 \times 2.32) + (0.1 \times 3.32) \\
&= 1.153.
\end{align*}

We now compare this to the extreme distributions
\begin{equation}
\bm{q} = (1,0,0), ~ ~ \bm{1} = (1/3, 1/3, 1/3),
\end{equation}
which are the certain and maximally uncertain distributions respectively. These then have entropy
\begin{align*}
H(X_{\bm{q}}) &= 0 ~ ~ ~ \textrm{and}  ~~ ~  H(X_{\bm{1}}) = \log_2\big(3\big)
\end{align*}

Given $\bm{q}$, there is no uncertainty in the outcome of the random variable, we therefore learn nothing when the outcome becomes known, and the entropy is zero.  

Given $\bm{1}$, there is maximum uncertainty in the outcome of the random variable, we therefore gain the maximum amount of information when the outcome becomes known, and the entropy is maximum.  

It can then be seen that, given $\bm{p}$, we have 
\begin{equation}
H(X_{\bm{q}}) \leq H(X_{\bm{p}}) \leq H(X_{\bm{1}}),
\end{equation}
meaning that the uncertainty before the outcome of the random variable becomes know, or the information gained after, sits between these two extreme distributions. 
:::

Through the [noiseless coding theorem](https://en.wikipedia.org/wiki/Shannon%27s_source_coding_theorem), the entropy has an operational interpretation, which gives it a solid grounding in practical reality: given a two outcome random variable with $X$, from which $k$ outputs have been collected, $kH(X)$ bits are needed to stored these $k$ outputs.  
 
### Generalised Entropies

Given a set of numbers that are distributed via some probability distribution, the mean is not the only function that can be used to aggregate the set of numbers.

Specifically, one can generalise the notion of means using [Kolmogorov–Nagumo averages](https://en.wikipedia.org/wiki/Quasi-arithmetic_mean). 

```{card} 
:header: [**Kolmogorov–Nagumo averages**](https://en.wikipedia.org/wiki/Quasi-arithmetic_mean)

Let $X = \{x_1, x_2, x_3, \ldots, x_n\}$ be a set of $n$ different numbers, and let $f(\cdot)$ be a continuous and injective (one-to-one) function. 

The $f-$mean of $X$ is 
\begin{equation}
M_f(X) = f^{-1} \biggl( \frac{1}{n} \sum_{i=1}^n f(x_i) \biggl).
\end{equation}

If $f(x) = ax+b$ for some constants $a$ and $b$, this reduces to the arithmetic mean.
```

Using the Kolmogorov–Nagumo averages, a general entropy function can then be defined as   
\begin{equation}
    H_{g}(X) = f^{-1} \bigg( \sum_{x=1}^n p_x f\big(I(p_x)\big) \bigg),
\end{equation}
where each element is weighted by its probability of occurring, rather then equally as in the definition of the Kolmogorov–Nagumo averages given above. 

Using this, it can be seen that the Shannon entropy is a special case of the $f-$mean of the information gain of a probability distribution where $f(x)=ax+b$. 

### $\alpha$-Rényi Entropies 

Rényi looked for functions $f(\cdot)$ that made $H_g(X)$ additive for two independent random variables, as this was a desirable feature of the Shannon entropy. In addition to $f(x)=ax+b$, it was found $f(x) = ce^{(\alpha-1)x}$ also made $H_g(X)$ additive, where $\alpha$ is a parameter and $c$ a constant. 

Using this for $c=1$ gives the so-called $\alpha$-Rényi Entropies:
\begin{equation}
    H_{\alpha}(X) = \frac{1}{1-\alpha} \log\bigg( \sum_{x=1}^n p_x^{\alpha} \bigg).
\end{equation}
For $\alpha=0,1,\infty$ it is defined via the limits towards these values. 

Just as different means inform us about different features of a set of numbers, the different Rényi entropies informs us about different features of the information gain of a distribution. 

It can be shown that 
\begin{equation}
\lim_{\alpha \rightarrow 1}  H_{\alpha}(X) = H(X),
\end{equation}
meaning that in the limit of $\alpha$ tending toward one, the Rényi entropy becomes the Shannon entropy. 

