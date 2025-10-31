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

Entropy functions are used throughout quantum information theory, often to bound the success performance in various operational tasks where information must processed in order to succeed. Broadly, they describe the level of uncertainty in a probability distribution. We will here provide a short summary of entropy functions. 

Consider a discrete random variable $X$, where the one gets the outcome $x$ with probability $p_x$. If there are $n$ possible outcomes, this can be described by the probability distribution $p=(p_1, p_2, p_3, \ldots, p_n)$, such that $p_x \geq 0$ and $\sum_{x=1}^n p_x=1$. If the outcome of the random variable is $y$, then the information gained from now knowing this is 
\begin{equation}
    I(p_y) = -\log(p_y).
\end{equation}
It can be seen that if the outcome $y$ occurs with high probability, then $I(p_y)$ is very small; if the outcome $y$ occurs with low probability, then $I(p_y)$ is very large. That is, we gain lots of information if we are surprised about the outcome i.e., it had a low probability of occurring. For this reason, the function $I(\cdot)$ is sometimes refereed to as the surprisal.  

The mathematical justifications for $I(\cdot)$ being the correct function for quantify the information gain is: 
\begin{itemize}
    \item The information gain should depend only on the probability of an given outcome occurring, not on its label. 
    \item The function should be a smooth function of probability. 
    \item $I(p_yp_z) = I(p_y) + I(p_z)$, meaning the information gained from two independent events occurring is the sum of the information gained from the individual events. 
\end{itemize}

The entropy of the random variable $X$ is then nothing more then the average information gain
\begin{equation}
    \begin{split}
            H(X) =  \mathbb{E} \big[ I(p_x) \big] &=  -\sum_{x=1}^n p_x \log(p_x) \\
    \end{split}
\end{equation}
This can be thought of as a measuring of the uncertainty before the outcome is known, or as a measure of how much information is gained after the outcome is known. 

Shannon also showed through his noiseless coding theorem that the entropy had an operational interpretation, giving it a grounding in practical reality. Specifically, given a random variable with $X$ from which $k$ outputs have been collected, $kH(X)$ bits are needed to stored these $k$ outputs.  
Once the outcome of the random variable becomes known,  

Although, the mean is not the only function that can be used to aggregate a set of numbers distributed via some probability distribution. In the most general case, one can use Kolmogorov–Nagumo averages. Using these, a general entropy function can be defined by  
\begin{equation}
    H_{g}(X) = f^{-1} \bigg( \sum_{x=1}^n p_x f(x) \bigg),
\end{equation}
where $f(\cdot)$ is continuous, invertible, and strictly monotonic. 

Rényi looked for functions $f(\cdot)$ that satasfied the above conditions but also made $H_g(X)$ additive for two independent random variables. He found $f(x) = e^{(\alpha-1)x}$  where $\alpha$ is a parameter. This gives the so-called $\alpha$-Rényi Entropies 
\begin{equation}
    H_{\alpha} = \frac{1}{1-\alpha} \log\bigg( \sum_{x=1}^n p_x^{\alpha} \bigg).
\end{equation}
for $\alpha=0,1,\infty$ it is defined via the limits towards these values. 

Just as different means inform us about different features of a distribution, the different Rényi entropies informs us about different features of the information about a distribution. 

It can be seen that as $\lim_{\alpha \rightarrow 1}  H_{\alpha} = H(X)$, meaning the limit as $\alpha$ tends to one of the Rényi entropy is the Shannon entropy. 



Entropies are functionals from elements in $\mathcal{H}$ to the real numbers. Broadly, they describe the level of uncertainty in a random variable. 