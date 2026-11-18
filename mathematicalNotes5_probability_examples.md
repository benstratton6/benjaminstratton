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

## Definitions

Probability aims to put a numerical value on how likely it is for different events to occur; it is a number between $0$ and $1$, where $0$ means it will never occur and $1$ means it will occur with certainty. 

The probability of outcome $A$ occurring can therefore be denoted as 
\begin{equation}
P(A) \in [0,1].
\end{equation}
If the event either happens or does not with certainty, then the probability that the event does not occur is given by 
\begin{equation}
1 - P(A).
\end{equation}

### Marginal Probability
Consider now two events, $A$ and $B$. The probability that event $A$ occurs independently of event $B$, denoted $P(A)$, is called the **marginal probability** of $A$. The marginal probability of event $B$ is then $P(B)$. 

### Joint Probability
The probability of both event $A$ and event $B$ occurring is called the **joint probability**, which is denoted
\begin{equation}
P(A \cap B) \in [0,1].
\end{equation}

### Conditional Probability
The probability of event $A$ occurring, given that event $B$ has already occurred, is called the **conditional probability**, and is denoted
\begin{equation}
P(A \vert B) \in [0,1].
\end{equation}

### Independent Events

Events $A$ and $B$ are **independent** if the occurrence of $B$ does not effect the probability of $A$ occurring. 

In this case, the following relationship between the marginal, joint and conditional probabilites apply: 
\begin{align*}
P(A \vert B) &= P(A) \\
P(B \vert A) &= P(B) \\
P(A \cap B) &= P(A) \times P(B)
\end{align*}

### Mutual Exclusivity

Events $A$ and $B$ are **mutually exclusive** if they cannot both occur at the same time. 

In this case, the joint probability of the two events, that is the probability that they both occur, must be zero:
\begin{equation}
P(A \cap B)=0.
\end{equation}

## Probability Equations

Here are some relationships between the marginal, joint and conditional probabilities. 

### Chain Rule of Probability

The chain rule of probability relates the marginal, joint and conditional probabilites of events $A$ and $B$ as
(chain_rule_probability_page)=
\begin{equation}
P(A \cap B) = P(A \vert B) \times P(B),
\end{equation}
meaning that the probability of both event $A$ and $B$ occurring is equal to the probability of event $A$ occurring given event $B$ has occurred, multiplied by the probability that event $B$ occurs. 

The rule extends to more events too. Consider now a third event, $C$. It then holds that 
\begin{equation}
P(A \cap B \cap C) = P(A \vert B, C) \times P(B \cap C),
\end{equation}
where $P(A \cap B \cap C)$ is the joint probability of events $A,B$ and $C$ occurring; $P(B \cap C)$ is the joint probability of events $B$ and $C$ occurring, and $P(A \vert B,C)$ is the probability of event $A$ occurring given that event $B$ and $C$ have occurred. 

### Bayes' theorem

Bayes' theorem relates the marginal distribution $P(A \vert B)$ to $P(B \vert A)$ as
(bayes_theorem_target_probability_page)=
\begin{equation}
P(A \vert B) = \frac{P(B \vert A)P(A)}{P(B)}.
\end{equation} 
It is commonly used to update the probability that an event $A$ will occur when some additional piece of evidence in the form of event $B$ has occurred. 

Note, Bayes' theorem arises from that fact the chain rule applies equally for both $A$ and $B$, such that
\begin{align*}
P(A \cap B) &= P(A \vert B) \times P(B) \\
P(A \cap B) &= P(B \vert A) \times P(A).
\end{align*}
Equating these two gives Bayes' rule. 

:::{dropdown} **Alternative Form of Bayes' theorem**

From the [chain rule](#chain_rule_probability_page) it holds that
\begin{equation}
P(A \vert B) = \frac{P(A \cap B)}{P(B)}.
\end{equation} 
As noted above, it also follows that 
\begin{equation}
P(A \cap B) = P(B \vert A) P(A).
\end{equation}
Now, denoting event $A$ not occurring by $\overline{A}$, it holds that 
\begin{align*}
P(B) &= P(A \cap B) + P(\overline{A} \cap B) \\
&= P(B \vert A)P(A) + P(B \vert \overline{A})P(\overline{A}).
\end{align*}.
Putting this together, one gets that 
\begin{equation}
P(A \vert B) = \frac{P(B \vert A) P(A)}{P(B \vert A)P(A) + P(B \vert \overline{A})P(\overline{A})}.
\end{equation} 
:::

## Probability Examples

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