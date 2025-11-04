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
In classical physics, any two distinct states of a physical system are distinguishable --- there always exists a measurement that can be made to tell the systems apart. In quantum mechanics, this is not generally the case. The task of quantum state discrimination studies these fundamental limitations on our ability to distinguish quantum states. 

## Quantum State Discrimination

Let $(p_x, \rho_x)$ be an ensemble, such that one gets the state $\rho_x$ with probability $p_x$. Assume this ensemble is known to both to a referee and a player. The referee then takes a state $\rho_y \in (p_x, \rho_x)$ from the ensemble and gives it to the player. The players makes a measurement on the state and outputs an index $z$. If $z=x$ the player succeeds at the task, if $z \neq x$ the player fails at the task. 

The ability of a player to succeed in the task of quantum state discrimination can be quantified by the maximum success probability,
\begin{align*}
    P_{\mathrm{suc}} &= \max_{\{T_x\}_x} \sum_x p_x \textrm{tr}\big[ T_x \rho_x \big] \\
    &\textrm{s.t} ~ ~ T_x \geq 0~\forall~x, ~ ~ \sum_x T_x = \mathbb{I},
\end{align*}
such that all POVM are optimised over. This is a Semidefinite Program and there therefore exists efficient classical methods for finding the optimal solution. Although, in general, there will not be a unique POVM that achieves this optimal. One can therefore choose the measurement strategy best suited for their experimental implementation. 

If $P_{\mathrm{suc}}=1$ then the player is always able to identify which state they have been given by the referee with certainty. Although, this is known to be possible if and only if the ensemble consists of only orthogonal states i.e, $P_{\mathrm{suc}}=1$ if and only if 
\begin{equation}
    \textrm{tr}\big[\rho_y\rho_z\big]=\delta_{y,z}~\forall~\rho_y, \rho_z \in (p_x, \rho_x).
\end{equation}

:::{dropdown} Proof
:open:
If $P_{\mathrm{suc}}=1$ then $\textrm{tr}\big[T_x\rho_x\big]=1~\forall~x$, as $\sum_x p_x = 1$ and $0 \leq p_x \leq 1$. As $\textrm{tr}\big[\rho_x\big]=1$, the following holds for all $x$,
\begin{equation}
        \textrm{tr}\big[(\mathbb{I} - T_x)\rho_x\big]= 0 ~ ~ \forall~x.
\end{equation}
As $\mathbb{I} - T_x \geq 0$ and $\rho_x \geq 0$ it can then be concluded that $(\mathbb{I} - T_x)\rho_x=0$, such that $T_x \rho_x = \rho_x$. 

From this, it can be seen that $T_x$ acts as the identity on the support of $\rho_x$ i.e., $T_x \Pi_x = \Pi_x$ where $\Pi_x$ is the projector onto the support of $\rho_x$. To see that this holds, consider $\rho \ketbra{\lambda_i} = \lambda_i \ketbra{\lambda_i}$, such that $\{ \ketbra{\lambda_i} \}_i$ are the eigenvectors of $\rho$. From this, it can be seen that $T_{x} \ketbra{\lambda_i} = \ketbra{\lambda_i}$ using $T_x \rho_x = \rho_x$. Finally, by noting that $\Pi_x = \sum_i \ketbra{\lambda_i}$, the condition is found. 

We conclude the proof by contradiction. Assume that the intersection between the supports of two arbitrary states is non-zero, meaning there exists a $\ketbra{\psi}$ such that
\begin{equation}
    \ketbra{\psi} \in \Pi_x \cap \Pi_y.
\end{equation}
Using $T_x \Pi_x = \Pi_x$ and $T_y \Pi_y = \Pi_y$ it can be seen that
\begin{equation}
    T_x \ketbra{\psi} = \ketbra{\psi}, ~ ~ ~ T_y \ketbra{\psi} = \ketbra{\psi},
\end{equation}
such that $(T_x + T_y)\ketbra{\psi} = 2 \ketbra{\psi}$. Then, using the fact that $\sum_z T_z = \mathbb{I}$, it can be seen that
\begin{equation}
    \begin{split}
        \mathbb{I} \ketbra{\psi} &= \sum_z T_z \ketbra{\psi} \\
        & = (T_x + T_y + \sum_{z \neq x,y} T_z) \ketbra{\psi}.  \label{}
    \end{split}
\end{equation}
Taking the trace of both sides we get $1 = 1 + 1 + \alpha$, where $\alpha = \sum_{z\neqx,y}\textrm{tr}\big[T_z \ketbra{\psi} \big] \geq 0$ as $\textrm{tr}\big[T_z \ketbra{\psi} \big] \geq 0 ~\forall z$ due to $T_z \geq 0~\forall~z$. This is of course a contradiction, meaning the above equation can only hold if $\ketbra{\psi}=0$. As this was done for two arbitrary states in the ensemble, it can be concluded that the intersections of the supports of all states in the ensemble must be zero. Hence, if $P_{\mathrm{suc}}=1$, then the states in the ensemble must be orthogonal. 

In the other direction, if the states in the ensemble are orthogonal, one can always create a POVM that includes the projectors onto the supports of all the states. Specifically, measuring the POVM
\begin{equation}
    \{ \Pi_x \}_x + T_{\mathrm{rest}}, ~ ~  T_{\mathrm{rest}} = \mathbb{I} - \sum_x \Pi_x,
\end{equation}
will allow quantum state discrimination to be performed with certainty. 
:::


    

