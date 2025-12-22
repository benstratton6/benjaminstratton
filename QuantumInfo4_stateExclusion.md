---
title: State Exclusion
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
keywords: State Exclusion, State Discrimination, POVMs, games.  
abstract: Details of the task of quantum state exclusion.   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(state_exclusion_page_target)=
The task of quantum state exclusion [](https://link.aps.org/doi/10.1103/PhysRevA.66.062111) [](https://doi.org/10.1038/nphys2309) [](http://dx.doi.org/10.1103/PhysRevA.89.022336) arises from a natural relaxation of the task of [quantum state discrimination](#quantum_state_discrimination_task) – particularly in scenarios where deterministic quantum state discrimination is impossible. In this task, a weaker aim is considered, with the player instead being asked to determine states from the set they _have_ _not_ been given by the referee.

## State Exclusion Overview 

```{card} 
:header: **Task of Quantum State Exclusion**
Let $(p_x, \rho_x)_x$ be an ensemble, such that one gets the state $\rho_x$ with probability $p_x$. Assume this ensemble is known to both a referee and a player. The referee then takes a state $\rho_y$ from the ensemble, with probability $p_y$, and gives it to the player. The players makes a measurement on the state and outputs a set of indices $\mathbb{G}$ of length $k$, where $k \leq \vert (p_x, \rho_x)_x \vert - 1$. 

If $y \notin \mathbb{G}$ the player succeeds at the task, if $y \in \mathbb{G}$ the player fails at the task. 
Card content
```
In the task of quantum state exclusion, the player therefore aims to identify $k$-states that they have _not_ been given to them by the referee. 

### 1-State Exclusion
If the player outputs a single label $g$ such that $g \neq x$ with certainty, this is conclusive $1$-state exclusion. This occurs if the player is able to find a [POVM](#POVM_measurement_definition_target) such that  
\begin{equation}
    \textrm{tr} \big[ T_{g}\rho_{g}] = 0 ~ ~ \forall ~~ g  \in \{1, \ldots ,N\}. \label{stateExclusionEquation}
\end{equation}
If the player gets the measurement outcome associated to $T_{g}$, they output $g$ knowing with certainty the referee could not have sent $\rho_{g}$.

In general, a POVM may not exists that can perform conclusive state exclusion. Instead, state exclusion can be performed with some error, as given by the following SPD: 
\begin{align*}
    \min &~~ P_{err} = \sum^{N}_{g}  \textrm{tr} \big[T_{g} \rho_{g}] \\
    \textrm{Subject to:}& ~ ~  \sum^{N}_{g} T_{g} = \mathbb{I}, ~~ T_{g} \geq 0 ~ \forall ~ g, 
\end{align*}
where $P_{err}$ is the probability of making an error when performing exclusion, meaning the probability of outputting the index $g=x$. 

### k-State Exclusion

If the player outputs a set of $k$ labels, $\{ g_{i} \}^{k}$, such that $g_{i} \neq x ~ \forall ~ g_{i} \in \{g_{i}\}^{k}$ with certainty, this is conclusive $k$-state exclusion. There are $N \choose k$ different sets of $k$ labels the player could exclude, corresponding to all the different subsets of $\{1,\ldots,N\}$ of length $k$. Therefore, when performing $k$-state exclusion the player aims to find a POVM with $N \choose k$ elements such that each measurement outcome allows the player to exclude a subset of states from $\{\rho_{x} \}^{N}$ of length $k$. 

#### k-State Exclusion as 1-State Exclusion

All $k$-state exclusion tasks can be recast as $1$-state exclusion tasks by reformulating the set $\{\rho_{x}\}^{N}$ [](http://dx.doi.org/10.1103/PhysRevA.89.022336). Conceptually, this means all $k$-state exclusion tasks have a $1$-state exclusion task that they are dual to, allowing all state exclusion tasks to be studied under the $1$-state exclusion framework. 

Let $Y_{(N, k)}$ be the set of all subsets of the integers $\{1,2,...,N\}$ of length $k$. The player aims to measure a POVM on a state $\sigma \in \{ \rho_{x} \}^{N}$, given to them by the referee, and output a set of labels $Y \in Y_{(N,k)}$ such that $\sigma \notin \{ \rho_{y} \}_{y \in Y}$. Such a measurement will be a POVM with $a = {N \choose k}$ terms as there are $a$ subsets of $\{1,2,...,N\}$ of length $k$. For each elements of this POVM, $S = \{S_{l}\}^{a}_{l=1}$, the following equation must hold, 
\begin{equation}
    \textrm{tr}\big[S_{Y}\rho_{y}] = 0 ~ \forall ~y~ \in~ Y. \label{multiStateExclusionEquations}
\end{equation}
By defining 
\begin{equation}
    \rho_{Y} = \sum_{y \in Y} \rho_{y}, 
\end{equation}
the $k$-state exclusion task can be expressed as the following set of equations
\begin{equation}
    \textrm{tr} \big[ S_{Y} \rho_{Y}] = 0 ~\forall~Y \in Y_{(N,K)}. 
\end{equation}
This is now the same form as the $1$-state exclusion task conditions. This is the dual $1$-state exclusion task to the $k$-state exclusion task. 

Using the dual $1$-state exclusion task, $k$-state exclusion can also now be formulated as an SPD: 
\begin{align*}
    \min & ~~ P^{k}_{err} = \sum_{Y} \textrm{tr}[S_{Y}\rho_{Y}] \\
    \textrm{Subject to:}& ~ ~ \sum^{N}_{i} S_{i} = \mathbb{I}, ~~ S_{i} \geq 0 ~ \forall ~ i,
\end{align*}

where $P^{k}_{err} > 0$ if no POVM to conclusively perform $k$-state exclusion exists. 

### $(N-1)$-State Exclusion

For an ensemble with $N$ states, performing conclusive $(N-1)$-state exclusion is equivalent to performing deterministic quantum state discrimination: knowing for certain $N-1$ states that you _do_ _not_ have is equivalent to knowing which state you _do_ have. Put alternatively, 
\begin{equation}
P^{N-1}_{\mathrm{err}} = 0 \iff P_{\mathrm{suc}} = 1,
\end{equation}
where $P_{\mathrm{suc}}$ is [maximum success probability](#state_discrimination_min_error_equation) in performing quantum state discrimination. 

As it is known that $P_{\mathrm{suc}} = 1$ [if and only if](#state_discrimination_deterministic) all states in the ensemble are orthogonal. Hence, $P^{N-1}_{\mathrm{err}} = 0$ if and only if all states in the ensemble are orthogonal. 

Conclusive state discrimination can therefore be considered to be a special case of conclusive $k$-state exclusion. How the two tasks are related in the non-conclusive case, and for $k< N-1$, remains an active area of research.

## Sub-Channel Exclusion

A closely related task to state exclusion is sub-channel exclusion. A special case of sub-channel exclusion concerns a collection of completely-positive trace non-increasing linear maps, $\Psi = \{\Psi_{x}\}_{x=1}^N$, such that $\sum_{x=1}^N \Psi_{x}$ is a channel. This collection is a [quantum instrument](https://en.wikipedia.org/wiki/Quantum_instrument), with each map $\Psi_{x}$ called a sub-channel.

In this task, a player has a reference state $\rho$ that they send to the referee. The referee then measures $ \rho $ using the instrument and returns the
post-measurement state to the player. The player measures a POVM on the state and outputs a label $g \in \{1, \ldots ,N\}$. They succeed if they output a label of a sub-channel that was not applied. As before, the player can output the label of a sub-channel not applied with certainty, they can output $k$ labels, $\{ g_{i} \}^{k}_{i=1}$, or they can output $k$ labels with certainty.

## Weak and Strong Exclusion

```{card} 
:header: **Strong State Exclusion**

Given a set of states $\{ \rho_{x} \}^{N}_{x=1}$, strong conclusive $1$-state exclusion is possible if there exists a POVM $T=\{T_{a}\}_{a=1}^{N}$ such that 
\begin{equation}
        \textnormal{tr} \big[ T_{x} \rho_{x} \big] = 0 \quad\forall~x\in\{1, \ldots, N\} \hspace{0.2cm} .
\end{equation}
**and**
\begin{equation}   
 \sum_{x=1}^{N} \textnormal{tr} \big[ T_{a} \rho_{x} ] \neq 0\quad\forall~a\in\{1,\ldots,N\}
\end{equation}

```

```{card} 
:header: **Weak State Exclusion**

Given a set of states $\{ \rho_{x} \}^{N}_{x=1}$, weak conclusive $1$-state exclusion is possible if there exists a POVM $T=\{T_{a}\}_{a=1}^{N}$ such that 
\begin{equation}
        \textnormal{tr} \big[ T_{x} \rho_{x} \big] = 0 \quad\forall~x\in\{1, \ldots, N\}.
\end{equation}

```

The additional condition in strong state exclusion ensures that all outcomes of the POVM $\{T_{a}\}_{a=1}^{N}$ have some probability of occurring. Strong conclusive $1$-state exclusion on the set $\{ \rho_{x} \}^{N}_{x=1}$ is defined to be the existence of an $N$ element POVM where each element excludes a different state from $\{ \rho_{x} \}^{N}_{x=1}$ with certainty. 

Weak conclusive $1$-state exclusion on $\{ \rho_{x} \}^{N}_{x=1}$ is defined to be the existence of a POVM with $L$ non-zero elements, where $L\leq N$, such that each conclusively exclude a different state from a subset of $\{ \rho_{x} \}^{N}_{x=1}$ of size $L$. Seen [](quantumStateExclusion) for an example. 

When extended to $k$-state exclusion, strong exclusion means that there exists a POVM that can exclude all possible sub-sets of $\{ \rho_{x} \}^{N}_{x=1}$ of length $k$. Weak exclusion then means that there exists a POVM that can only exclude {\em some subsets} of $\{ \rho_{x} \}^{N}_{x=1}$ of length $k$. Note, this is equivalent to considering strong and weak exclusion on the equivalent $1$-state exclusion task. 

```{figure} quantum_information_state_exclusion_image
:label: quantumStateExclusion
:alt: Sunset at the beach
:align: center

A figure showing the difference between strong state exclusion and weak state exclusion. 
```

:::{dropdown} Further Details

It is clearly the case from the above definitions that weak state exclusion is a requisite for strong state exclusion – justifying their respective names. Moreover, if one is able to perform strong state exclusion, they can trivially convert this into weak state exclusion via classical post-processing of the measurement outcomes. It can also be seen that if any of the states in $\{ \rho_{x} \}^{N}_{x=1}$ are full-rank, then strong state exclusion is never possible. This is due to $\textrm{tr}[T_{g}\rho_{x}] = 0$ if and only if $T_{g} = 0$ when $\rho_{x}$ is full-rank.

The above definition of strong conclusive $1$-state exclusion on $N$ states means it is defined as the existence of an $N$ element POVM where each element excludes a different state from $\{ \rho_{x} \}^{N}_{x=1}$ with certainty. It can be the case that some POVM elements exclude multiple states, but each element must exclude at least one different state. The above definition of weak conclusive $1$-state exclusion given above is then defined to be the existence of a POVM with $L$ non-zero elements (where $L\leq N$) that each conclusively exclude a different state from a subset of $\{ \rho_{x} \}^{N}_{x=1}$ of size $L$. Using this terminology, one could define the ability to perform weak state exclusion on $\{ \rho_{x} \}^{N}_{x=1}$ as the ability to perform strong state exclusion on some subset of $\{ \rho_{x} \}^{N}_{x=1}$. 

Previously, weak state exclusion has been used as the general definition of state exclusion. However, this definition has attracted (indirect) criticism for trivialising the problem of state exclusion, as if a player can perform conclusive $1$-state exclusion on any two states $\{\rho_1, \rho_2\}\subseteq\{ \rho_{x} \}^{N}_{x=1}$ using the two-element POVM $\{M_{1}, M_{2}\}$, then by definition $1$-state exclusion could trivially be performed on the whole set $\{ \rho_{x} \}^{N}_{x=1}$ by considering the $N$ element POVM
\begin{equation}
    \{T_{1} = M_{1}, T_{2} = M_{2}, T_{3} = 0, ~\ldots~, T_{N} = 0\}.
\end{equation}
Each measurement outcome would exclude one state, but some states would never be excluded. Whilst such an example is indeed trivial, there exist plenty of intermediate scenarios between this and strong state exclusion that could prove useful in operationally motivated tasks. 

:::

