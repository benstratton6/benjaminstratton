---
title: Pauli Group
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
keywords: Pauli Operators, Qubits, Complete Basis.   
abstract: Details, properties and applications of the Pauli Group   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(Pauli_group_page_target)=
The Pauli Group is a [group](https://en.wikipedia.org/wiki/Group_(mathematics)) formed by taking the tensor product of the Pauli operators and the identity operator. It consists of all combinations of the tensor products with phases $\{\pm 1, \pm i \}$. 

## Single Qubit Group

The Pauli operators in the computational basis are 
\begin{equation}
X = \sigma_1 = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, ~ ~ Y = \sigma_2 =\begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}, ~ ~ Z = \sigma_3 = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}.
\end{equation}

They multiple as 
\begin{equation}
\sigma_{i} \sigma_j = \delta_{ij}\mathbb{I} + i \epsilon_{ijk} \sigma_k
\end{equation}
where $\epsilon_{ijk}$ is the [Levi-Civita symbol](#Levi_Civita_symbol_target_bloch) and $\mathbb{I}$ is the identity operator. 

Hence, by multiplying any combinations of the Pauli operators together one will always get a Pauli operator with a phase of either $\pm 1$ or $\pm i$. Therefore, they form a group. 

```{card} 
:header: **Single Qubit Pauli Group**

The single qubit Pauli group is 
\begin{align*}
\mathcal{P}_1 &\coloneqq \langle X, Z, i \mathbb{I} \rangle \\
&= \{ \pm \mathbb{I}, \pm i \mathbb{I}, \pm {X}, \pm i {X}, \pm {Y}, \pm i {Y}, \pm {Z}, \pm i {Z} \}.
\end{align*}
 
```

Note, in the above we have give the [generator](#group_generator_definition) of the Pauli-group, denoted as $\langle \cdot \rangle$, using the fact that $Y=i XZ$.

## n-Qubit Pauli Group

The $n$-qubit Pauli group is then given by the tensor product of the elements of the single qubit Pauli-group $\mathcal{P}_1$. 

```{card} 
:header: **$n$-qubit Pauli Group**

The $n$-qubit Pauli group is 
\begin{align*}
\mathcal{P}_n &\coloneqq \{ P_1 \otimes P_2 \otimes P_3 \otimes ... \otimes P_n : P_i \in \mathcal{P}_1~\forall~i \in [1, n] \}.
\end{align*}

The group has $4^{n+1}$ elements, as there are $4^n$ different combinations of tensor products of $\{X, Y, Z, \mathbb{I} \}$ of length $n$, with the group containing each potential combination with a phase of $\pm 1$ and $\pm i$. 

```

### Properties

1. All elements of $\mathcal{P}_n$ square to $\pm \mathbb{I}$,  
    \begin{equation}
    P_j^2 = P_j P_j = \pm \mathbb{I} ~\forall~P_j \in \mathcal{P}_n.
    \end{equation}
    :::{dropdown} Proof

    It can be seen that the square of any single qubit Pauli operator is the identity: 
    \begin{equation}
    \sigma_j^2 = \sigma_j \sigma_j = \mathbb{I} ~ \forall ~j. 
    \end{equation}

    Ignoring the global phase, the square of any $P_j \in \mathcal{P}_n$ is then
    \begin{align*}
    P_j^2 = P_jP_j &= P^1_jP^1_j \otimes P^2_jP^2_j \otimes \ldots \otimes P^n_jP^n_j \\
    &= \mathbb{I}_2 \otimes \mathbb{I}_2 \otimes \ldots \mathbb{I}_2 \\
    &= \mathbb{I}_{2^n}, 
    \end{align*} 
    where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$, and $\mathbb{I}_d$ is the identity operator of dimension $d$. 

    One then just needs to consider the global phase $\beta \in \{\pm 1, \pm i\}$. It can be seen that $1^2=1$ and $(-1)^2=1$, whilst $i^2=-1$ and $(-i)^2=-1$. Hence, if the global phase is real then the element squares to positive identity; if the global phase is complex then the element squares to negative identity. 
    :::

2. All elements of $\mathcal{P}_n$ are either Hermitian or anti-Hermitian
    \begin{equation}
    P_j^\dagger = \pm P_j ~ \forall~P_j \in \mathcal{P}_n
    \end{equation}
    :::{dropdown} Proof

    It can be seen that all single qubit Pauli operators are Hermitian: 
    \begin{equation}
    \sigma_j^\dagger = \sigma_j ~ \forall ~j. 
    \end{equation}

    The adjoint of any $P_j \in \mathcal{P}_n$ is then 
    \begin{align*}
    P_j^\dagger &= \beta^* \big(P^1_j \otimes P^2_j \otimes \ldots \otimes P^n_j\big)^\dagger \\
    &= \beta^* (P^1_j)^\dagger \otimes (P^2_j)^\dagger \otimes \ldots \otimes (P^n_j)^\dagger \\
    &= \beta^*P^1_j \otimes P^2_j \otimes \ldots \otimes P^n_j \\
    \end{align*} 
    where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$, and $\beta \in \{\pm 1, \pm i \}$ is the overall phase of the element. 

    As $1^*=1$ and $(-1)^*=-1$, whilst $i^*=-i$ and $(-i)^*=i$, it can be seen that if the overall phase is real then the element is Hermitian, whereas if the overall phase is complex then the element is anti-Hermitian. 
    :::

3. All elements of $\mathcal{P}_n$ are unitary,
    \begin{align*}
    P_jP_j^\dagger &= P_j^\dagger P_j = \mathbb{I}~\forall~P_j \in \mathcal{P}_n
    \end{align*}
    :::{dropdown} Proof

    It can be seen that all single qubit Pauli operators are unitary: 
    \begin{equation}
    \sigma_j^\dagger \sigma_j = \sigma_j \sigma_j^\dagger = \mathbb{I}~ \forall ~j. 
    \end{equation}
    Moreover, the square of any single qubit Pauli operator is the identity: 
    \begin{equation}
    \sigma_j^2 = \sigma_j \sigma_j = \mathbb{I} ~ \forall ~j. 
    \end{equation} 

    The adjoint of any $P_j \in \mathcal{P}_n$ is then 
    \begin{align*}
    P_j^\dagger &= \beta^* \big(P^1_j \otimes P^2_j \otimes \ldots \otimes P^n_j\big)^\dagger \\
    &= \beta^* (P^1_j)^\dagger \otimes (P^2_j)^\dagger \otimes \ldots \otimes (P^n_j)^\dagger \\
    &= \beta^*P^1_j \otimes P^2_j \otimes \ldots \otimes P^n_j \\
    \end{align*} 
    where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$, and $\beta \in \{\pm 1, \pm i \}$ is the overall phase of the element. 

    Hence,
    \begin{align*}
    P_j P_j^\dagger &= \beta \beta^* (P^1_jP^1_j\otimes P^2_jP^2_j \otimes \ldots \otimes P^n_jP^n_j) \\
    &= \mathbb{I}
    \end{align*}
    as $\beta \beta^* = 1 ~\forall ~ \beta \in \{\pm 1, \pm i \}$ and all single qubit Pauli operators square to the identity. The same argument can be made for $P_j^\dagger P_j$.    

    :::

4. All elements of $\mathcal{P}_n \setminus \mathbb{I}$ are traceless,
    \begin{equation}
    \textrm{tr}\big[P_j \big] = 0 ~ \forall~P_j \in \mathcal{P}_n \setminus \mathbb{I}
    \end{equation}
    :::{dropdown} Proof

    It can be seen that all single qubit Pauli operators are traceless: 
    \begin{equation}
    \textrm{tr}\big[\sigma_j \big] = 0 ~ \forall ~j. 
    \end{equation}

    The trace of of any $P_j \in \mathcal{P}_n$ is then 
    \begin{align*}
    \textrm{tr}\big[P_j \big] &= \beta \textrm{tr}\big[ P^1_j \otimes P^2_j \otimes \ldots \otimes P^n_j \big] \\
    &= \beta \textrm{tr}\big[ P^1_j \big] \otimes \textrm{tr}\big[ P^2_j \big] \otimes \ldots \otimes \textrm{tr}\big[ P^n_j \big] \\
    &= 0.
    \end{align*} 
    where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$, and $\beta \in \{\pm 1, \pm i \}$ is the overall phase of the element. For $P_q \neq \mathbb{I}$, at least one $P_q^\alpha$ can not be equal to the identity. 

    Hence, it can be seen that if the operator at any location of the Pauli string is not the identity then the trace will be zero. 

    :::

5. Given any two elements of $\mathcal{P}_n$, they either commute or anti-commute i.e.,
    \begin{equation}
    P_lP_j = \pm P_jP_l ~\forall~P_l, P_j \in \mathcal{P}_n.
    \end{equation}
    :::{dropdown} Proof
     
    Consider two single qubit Pauli operators $\sigma_l$ and $\sigma_j$. 
    
    It can be seen that if $l=j$, then the Pauli operators trivially commute. If $l \neq j$, then they anti-commute, as
    \begin{align*}
    \sigma_l \sigma_j = i \epsilon_{ljk} \sigma_k \\
    \sigma_j \sigma_l = i \epsilon_{jlk} \sigma_k. \\
    \end{align*}
    From here, it can be seen that $(l,j,k) \rightarrow (j,l,k)$ is an odd permutation. Then, given that the combination of two odd permutations is then an even permutation, if $(l,j,k)$ is an odd permutation of $(1,2,3)$ then $(j,l,k)$ is an even permutation, and vice versa. Hence, $\epsilon_{ljk} = - \epsilon_{jlk}$, meaning that $\sigma_l \sigma_j = - \sigma_j \sigma_l$ if $l \neq j$. 

    Therefore, when consider the commutator of single qubit Pauli operators and the identity, if both operators are the same, or one is the identity, then they commute. Otherwise they anti-commute. One can therefore say that whenever the commutator is _non-trivial_, they anti-commute.

    Now consider two Pauli strings $P_l, P_k \in \mathcal{P}_n$, where we can ignore the global phase as 
    \begin{equation}
    \beta \gamma = \gamma \beta ~\forall~\beta, \gamma \in \{\pm 1, \pm i\},
    \end{equation} 
    i.e., all scalar commute. Due to the tensor product structure of the Pauli group elements, it can be seen that 
    \begin{align*}
      P_lP_j &= P^1_l P_j^1 \otimes P^2_l P_j^2 \otimes \ldots \otimes P^n_l P_j^n \\
      P_j P_l &= P^1_j P_l^1 \otimes P^2_j P_l^2 \otimes \ldots \otimes P^n_j P_l^n,
    \end{align*}
     where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$.

    The single Pauli operator at each location will then commute or anti-commute. It can be seen that if the number of locations where it anti-commutes is even then the whole Pauli string commutes; if the number of locations where it anti-commutes is odd then the whole Pauli string anti-commutes. 

    To determine if two Pauli string commute or anti-commute, one therefore needs to count the number of locations where the Pauli-strings intersect non-trivially.   
    :::

6. All elements of $\mathcal{P}_n \setminus \mathbb{I}$ have eigenvalues $\pm 1$, where the $+1$ and $-1$ degenerate eigenspaces are of equal dimension. 
    :::{dropdown} Proof

    Add Proof 
    :::

7. $\mathcal{P}_n$ forms a complete basis for the space of $2^n \times 2^n$ dimension complex matrices. 
    :::{dropdown} Proof

    Add Proof 
    
    :::