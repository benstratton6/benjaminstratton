---
title: Probability
subject: Tutorial
subtitle: 
# short_title: How to MyST
authors:
  - name: Benjamin Stratton
    # affiliations:
    #   - Executable Books
    #   - Curvenote
    orcid: 0009-0001-2746-3668
    email: ben.stratton@bristol.ac.uk
license: 
keywords: Probability. 
abstract: Here are a few interesting problems that highlight non-trivial aspects of probability. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

The problems presented here were discussed during a Bristol Quantum Information Theory group meeting, they taught me something about probability so I thought I would share them here. 

(problem_1)=
```{card} 
:header: **Problem 1** 

A couple has two children. One of the children is a $\mathrm{Boy}$. What is the probability that their other child is a $\mathrm{Girl}$? 

Assume that the probability of a $\mathrm{Boy}$ or $\mathrm{Girl}$ being born is equal. 

:::{dropdown} Solution

This problem can be solved by first considering the number of different possible combinations of two children. Assuming each child can only be a $\mathrm{Boy}$ or a $\mathrm{Girl}$ (such that we have only two possible outcomes), there are four possible ways to have two children:
\begin{equation}
(\mathrm{Boy}, \mathrm{Boy}), ~ (\mathrm{Boy}, \mathrm{Girl}), ~ (\mathrm{Girl}, \mathrm{Boy}), ~(\mathrm{Girl}, \mathrm{Girl}).
\end{equation} 
Now, we know that one of the children is a $\mathrm{Boy}$, hence the option ($\mathrm{Girl}$, $\mathrm{Girl}$) cannot occur.

This leaves the following possible combinations that have at least one $\mathrm{Boy}$:
\begin{equation}
(\mathrm{Boy}, \mathrm{Boy}), ~ (\mathrm{Boy}, \mathrm{Girl}), ~ (\mathrm{Girl}, \mathrm{Boy}).
\end{equation} 
Of these three possible combinations, two contain a $\mathrm{Girl}$. 

The probability that the second child is a $\mathrm{Girl}$ given the first is a $\mathrm{Boy}$ is then 
\begin{align*}
\frac{\mathrm{Number~of~ possible~ outcomes ~compatible~ with ~the ~future}}{\mathrm{Total~ of~ possible ~outcomes~ compatible~ with ~the~ prior}} = \frac{2}{3},
\end{align*}
As of the three possible outcomes above that all contained at least one $\mathrm{Boy}$, only two of the three also contained a $\mathrm{Girl}$.

An easy way to understand and expand this problem is by rephrasing it as **bit-strings**. Firstly, let 
\begin{equation}
\mathrm{Boy} \rightarrow 0, ~ ~ \mathrm{Girl} \rightarrow 1,
\end{equation}
such that the four possibilities become the set of two-bit-string,
\begin{equation}
\mathbb{B}_2 = \big\{ 00, 01, 10, 11 \big\}.
\end{equation}
The condition that one child is a $\mathrm{Boy}$ states that we want to only consider the bit-strings with at least one $0$,
\begin{equation}
\mathbb{B}_2^{P} = \big\{00, 01, 10 \big\} \subseteq \mathbb{B}_2,
\end{equation}
where the superscript $P$ stands for prior. 

The condition that the other child is a $\mathrm{Girl}$ then ask, of this reduced set of bit-strings $\mathbb{B}_2^{P}$, how many of the bit-string have a $1$:
\begin{equation}
\mathbb{B}_2^{F} = \big\{ 01, 10 \big\} \subseteq \mathbb{B}_2^{P},
\end{equation} 
where the superscript $P$ stands for future.

The probability of this situation occurring is then given by 
\begin{equation}
\mathrm{Prob} = \frac{\vert \mathbb{B}_2^{F} \vert}{\vert \mathbb{B}_2^{P} \vert}.
\end{equation}
Using this notation it is easy to see that a question of this form is really just a problem of counting bit-strings. 

The problem can now be expanded: **if one has ten children, nine of which are a $\mathrm{Boys}$, what is the probability that the tenth is a $\mathrm{Girl}$?** 

This question can then be rephrased as: _of the ten-bit-strings with nine $0$s, how many have one $1$_?

There are eleven ten-bit-strings with nine $0$s. Of these eleven, ten have one $1$. Hence, the probability of this occurring is given by 
\begin{equation}
\frac{10}{11}.
\end{equation}

One can use the counting bit-string notion to now answer this problem for an arbitrary amount of $\mathrm{Boy}$s or $\mathrm{Girl}$s occurring. Moreover, any binary variable with equal probability of outcome could be treated this way. 

:::

``` 

(problem_2)=
```{card} 
:header: **Problem 2** 

A couple has two children. Their **first** child is a $\mathrm{Boy}$. What is the probability that their **second** child is a $\mathrm{Girl}$? 

Assume that the probability of a $\mathrm{Boy}$ or $\mathrm{Girl}$ being born is equal. 

:::{dropdown} Solution

One can again use the bit-string notion developed above to answer this problem.

Assuming that the first bit represents the first born child and the second bit represents the second, this question asks: _of the two-bit-strings with a $0$ as the first bit, how many have a $1$ in the second bit_?. 

We now have 
\begin{equation}
\mathbb{B}_2^{P} = \big\{00, 01 \big\},
\end{equation}
and 
\begin{equation}
\mathbb{B}_2^{F} = \big\{ 01 \big\} \subseteq \mathbb{B}_2^{P},
\end{equation}

From this, the probability can easily be found as  
\begin{equation}
\frac{\vert \mathbb{B}_2^{F} \vert}{\vert \mathbb{B}_2^{P} \vert} = \frac{\vert \big\{ 01 \big\} \vert}{\vert \big\{ 00, 00 \big\} \vert} = \frac{1}{2}.
\end{equation}

Interestingly, this probability remains the same for an number of children when the order of children is specified. If one lists the prior children in order i.e., 
\begin{equation}
\mathbf{First}: \mathrm{Boy}, ~\mathbf{Second}:  \mathrm{Girl}, ~\mathbf{Third}: \mathrm{Girl} ... ~\mathbf{n}th: \mathrm{Boy},
\end{equation} 
the some $n$-bit-string $i_p \in \{0,1\}^{\times n}$ has been specified. When now considering the $(n+1)$-bit-strings to model another child, there will always be only two $(n+1)$-bit-strings that have $i_p$ as its first $n$ bits: $i_p0$ and $i_p1$. Hence, 
\begin{equation}
\mathbb{B}^{P}_{(n+1)} = \big\{ i_p0, i_p1 \big\}, ~ ~ \mathbb{B}^{F}_{(n+1)} = \big\{ i_p1 \big\},
\end{equation}
such that probability given this prior will always be $1/2$.   
:::
```