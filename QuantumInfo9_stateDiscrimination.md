---
title: State Discrimination
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
keywords: State Discrimination, POVMs, games.  
abstract: Details of the task of quantum state discrimination.   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(state_discrimination_page_target)=
In classical physics, any two distinct states of a physical system are distinguishable - there always exists a measurement that can be made to tell the systems apart. In quantum mechanics, this is not generally the case. The task of quantum state discrimination studies these fundamental limitations on our ability to distinguish quantum states. 

## Quantum State Discrimination
(quantum_state_discrimination_task)=
```{card} 
:header: **Task of Quantum State Discrimination**

Let $(p_x, \rho_x)_x$ be an ensemble, such that one gets the state $\rho_x$ with probability $p_x$. Assume this ensemble is known to both to a referee and a player. The referee then takes a state $\rho_y$ from the ensemble and gives it to the player. The players makes a measurement on the state and outputs an index $g$. 

If $g=x$ the player succeeds at the task, if $g \neq x$ the player fails at the task. 
```

The task of quantum state discrimination therefore asks the player to correctly identify which state from the ensemble they have been given by the referee. To succeed in this task, one should typically consider performing a measurement with $N \geq \vert (p_x, \rho_x)_x \vert$ different possible outcomes, where $\vert (p_x, \rho_x)_x \vert$ is the number of different states in the ensemble. Hence, each state in the ensemble is assigned a different measurement outcome. 

As the post measurement state is not considered, this measurement can be modelled by a [POVM](#POVM_measurement_definition_target). To the state $\rho_g$ from the ensemble a POVM element $T_g$ is assigned, such that if the player gets the outcome associated to $T_g$ they output the index $g$. The probability of outputting the index $g$ given the player has $\rho_g$ is then $\textrm{tr}\big[T_g\rho_g\big]$. This is therefore the probability that the player is successful in the task given the referee gave them $\rho_g$. 

One way of quantifying the ability of a player to succeed in the task of quantum state discrimination is the maximum success probability,
(state_discrimination_min_error_equation)=
\begin{align*}
    P_{\mathrm{suc}} &= \max_{\{T_x\}_x} \sum_x p_x \textrm{tr}\big[ T_x \rho_x \big] \\
    &\textrm{s.t} ~ ~ T_x \geq 0~\forall~x, ~ ~ \sum_x T_x = \mathbb{I},
\end{align*}
such that all POVM are optimised over. This is a semi-definite Program (SDP) and there therefore exists efficient classical methods for finding the optimal solution. Although, in general, there will not be a unique POVM that achieves this optimal. One can therefore choose the measurement strategy best suited for their experimental implementation. 

### Deterministic Discrimination
(state_discrimination_deterministic)=
If $P_{\mathrm{suc}}=1$ then the player is always able to identify which state they have been given by the referee with certainty. Although, this is known to be possible if and only if the ensemble consists of only orthogonal states i.e, $P_{\mathrm{suc}}=1$ if and only if 
\begin{equation}
    \textrm{tr}\big[\rho_y\rho_z\big]=\delta_{y,z},
\end{equation}
for all pairs $\rho_y, \rho_z$ in the ensemble.
:::{dropdown} Proof

If $P_{\mathrm{suc}}=1$ then $\textrm{tr}\big[T_x\rho_x\big]=1~\forall~x$, as $\sum_x p_x = 1$ and $0 \leq p_x \leq 1$. 

As $\textrm{tr}\big[\rho_x\big]=1$, the following holds for all $x$,
\begin{equation}
        \textrm{tr}\big[(\mathbb{I} - T_x)\rho_x\big]= 0 ~ ~ \forall~x.
\end{equation}
As $\mathbb{I} - T_x \geq 0$ and $\rho_x \geq 0$ it can then be concluded that $(\mathbb{I} - T_x)\rho_x=0$ such that $T_x \rho_x = \rho_x$. 

From this, it can be seen that $T_x$ acts as the identity on the support of $\rho_x$ i.e., 
\begin{equation}
T_x \Pi_x = \Pi_x,
\end{equation}
where $\Pi_x$ is the projector onto the support of $\rho_x$. To see that this holds, let $\{ \vert \lambda_i \rangle \langle \lambda_i \vert \}_i$ be the eigenvectors of $\rho$, such that 
\begin{equation}
\rho = \sum_i \lambda_i \vert \lambda_i \rangle \langle \lambda_i \vert.
\end{equation}
Then, 
\begin{equation}
\rho \vert \lambda_i \rangle \langle \lambda_i \vert = \lambda_i \vert \lambda_i \rangle \langle \lambda_i \vert.
\end{equation}
From this, it can be seen that
\begin{equation}
T_{x} \vert \lambda_i \rangle \langle \lambda_i \vert = \vert \lambda_i \rangle \langle \lambda_i \vert
\end{equation}
using the fact that $T_x \rho_x = \rho_x$. Finally, by noting that $\Pi_x = \sum_i \vert \lambda_i \rangle \langle \lambda_i \vert$, the condition is found. 

We conclude the proof by contradiction. Assume that the intersection between the supports of two arbitrary states in the ensemble $\rho_x$ and $\rho_y$ is non-zero, meaning there exists a $\vert \psi \rangle \langle \psi \vert$ such that
\begin{equation}
    \vert \psi \rangle \langle \psi \vert \in \Pi_x \cap \Pi_y,
\end{equation}
where $\Pi_x$ and $\Pi_y$ are the projectors onto the supports of $\rho_x$ and $\rho_y$ respectively. Using the facts that $T_x \Pi_x = \Pi_x$ and $T_y \Pi_y = \Pi_y$, it can be seen that
\begin{equation}
    T_x \vert \psi \rangle \langle \psi \vert = \vert \psi \rangle \langle \psi \vert, ~ ~ ~ T_y \vert \psi \rangle \langle \psi \vert = \vert \psi \rangle \langle \psi \vert.
\end{equation}
Hence, $(T_x + T_y)\vert \psi \rangle \langle \psi \vert = 2 \vert \psi \rangle \langle \psi \vert$. Then, using the fact that $\sum_z T_z = \mathbb{I}$, it can be seen that
\begin{equation}
    \begin{split}
        \mathbb{I} \vert \psi \rangle \langle \psi \vert &= \sum_z T_z \vert \psi \rangle \langle \psi \vert \\
        & = (T_x + T_y + \sum_{z \neq x,y} T_z) \vert \psi \rangle \langle \psi \vert.  
    \end{split}
\end{equation}
Taking the trace of both sides, we get that $1 = 1 + 1 + \alpha$, where 
\begin{equation}
\alpha = \sum_{z \neq x,y}\textrm{tr}\big[T_z \vert \psi \rangle \langle \psi \vert \big] \geq 0,
\end{equation}
as $\textrm{tr}\big[T_z \vert \psi \rangle \langle \psi \vert \big] \geq 0 ~\forall z$ due to $T_z \geq 0~\forall~z$ and $\vert \psi \rangle \langle \psi \vert \geq 0$. 

This is therefore a contradiction, with the above equation holding if and only if $\vert \psi \rangle \langle \psi \vert=0$. As this was done for two arbitrary states in the ensemble, it can be concluded that the intersections of the supports of all states in the ensemble must be zero if $P_{\mathrm{suc}}=1$.

In the other direction, if all the states in the ensemble are orthogonal, one can always create a POVM that includes the projectors onto the supports of all the states. Specifically, measuring the POVM
\begin{equation}
    \{ \Pi_x \}_x + T_{\mathrm{rest}}, ~ ~  T_{\mathrm{rest}} = \mathbb{I} - \sum_x \Pi_x,
\end{equation}
will allow quantum state discrimination to be performed with certainty. 
:::

### Unambiguous State Discrimination

An alternative strategy for claiming optimality is unambiguous state discrimination [](https://doi.org/10.48550/arXiv.1707.02571), where a measurement with $(N+1)$ outcomes is used if $N = \vert (p_x, \rho_x)_x \vert$. The aim here is that the index $g$ is output if and only if $g=x$, meaning the player outputs an index if and only if they are certain it relates to the state that they were given by the referee. This comes at the expense of the additional measurement outcome that gathers all the uncertain outcomes, with the player outputting that they are uncertain what state they have if they get this outcome, i.e., if the player gets the $(N+1)$th outcome they output `don't know' rather than an index. 

It will not always be possible to find such a POVM, with characterisations for what sets of states this is possible for being detailed in [](https://doi.org/10.1016/S0375-9601(98)00064-4), [](10.1103/PhysRevA.68.010301). As with the maximum success probability, success in unambiguous state discrimination can be cast as an SDP. Although, success now means minimising the probability of the player outputting `don't know'. 

    

