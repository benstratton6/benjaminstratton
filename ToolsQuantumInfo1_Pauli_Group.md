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
The Pauli Group is a [group](#group_page_group_definition) formed by taking the tensor product of the Pauli operators and the identity operator. It consists of all combinations of the tensor products with phases $\{\pm 1, \pm i \}$. 

## Single Qubit Group

The Pauli operators in the computational basis are 
(single_qubit_pauli_operators_target)=
\begin{equation}
X = \sigma_1 = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, ~ ~ Y = \sigma_2 =\begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}, ~ ~ Z = \sigma_3 = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}.
\end{equation}

They multiple as 
(single_qubit_pauli_multiplication)=
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

### Single Qubit Commutator Relation

The single qubit Pauli operators commute as 
\begin{equation}
[\sigma_j, \sigma_k] = 2 i \epsilon_{jkl} \sigma_l
\end{equation}
where, as above, $\epsilon_{ijk}$ is the [Levi-Civita symbol](#Levi_Civita_symbol_target_bloch) and $i = \sqrt{-1}$.  

:::{dropdown} Explicit Commutator Relations

\begin{align*}

&[X, X] = 0, \\
&[X, Y] = 2i Z, \\
&[X, Z] = -2iY, \\
& \\
&[Y, X] = -2i Z, \\
&[Y, Y] = 0, \\
&[Y, Z] = 2i X \\
& \\
&[Z, X] = 2iY, \\
&[Z, Y] = -2i X, \\
&[Z, Z] = 0, 

\end{align*}
:::

## n-Qubit Pauli Group

The $n$-qubit Pauli group is then given by the tensor product of the elements of the single qubit Pauli-group $\mathcal{P}_1$. 

```{card} 
:header: **$n$-qubit Pauli Group**

The $n$-qubit Pauli group is 
\begin{align*}
\mathcal{P}_n &\coloneqq \big\{ \beta P_1 \otimes P_2 \otimes P_3 \otimes ... \otimes P_n : P_j \in \mathcal{P}_1~\forall~j, \beta \in \{\pm 1, \pm i \} \big\}.
\end{align*}

The group has $4^{n+1}$ elements, as there are $4^n$ different combinations of tensor products of $\{X, Y, Z, \mathbb{I} \}$ of length $n$, with the group then containing each potential combination with a phase of $\pm 1$ and $\pm i$. 

An important subset of the Pauli-group is the Pauli-strings
\begin{align*}
\mathcal{P}^s_n &\coloneqq \big\{ P_1 \otimes P_2 \otimes P_3 \otimes ... \otimes P_n : P_j \in \mathcal{P}_1~\forall~j \big\} \subset \mathcal{P}_n, 
\end{align*}
which are the elements of the Pauli-group with global phase $+1$. 
```

### Generators

The $n$-qubit Pauli group is defined in terms of generators as 
\begin{equation}
\mathcal{P}_n = \langle X_j, Z_j, i \mathbb{I} \rangle_{j \in \{1,n\}}
\end{equation}
where $X_j$ and $Z_j$ act as the single qubit $X$ and $Z$ operators on the $j$th qubit respectively, and the identity everywhere else. 

### Properties

Below we highlight and prove key properties of the Pauli-group and the set of Pauli-strings. 

1. All elements of $\mathcal{P}_n$ square to $\pm \mathbb{I}$, 
    (property_1_of_Pauli_Strings)=
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
    (property_4_Pauli_strings)=
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
(eigenvalues_of_pauli_strings_target)=
6. All Hermitian elements of $\mathcal{P}_n \setminus \mathbb{I}$ have eigenvalues $\pm 1$, where the $+1$ and $-1$ degenerate eigenspaces are of equal dimension. 

    All non-Hermitian elements of $\mathcal{P}_n$ have eigenvalues $\pm i$, where the $+i$ and $-i$ degenerate eigenspaces are of equal dimension.
    :::{dropdown} Proof
    Let $P$ be a Hermitian element of $\mathcal{P}_n \setminus \mathbb{I}$.

    The vector $\ket{\psi}$ is an eigenvector of the Pauli-string $P$ with eigenvalue $\lambda$ if 
    \begin{equation}
    P \ket{\psi} = \lambda \ket{\psi}.
    \end{equation}
    From here, it can be seen that 
    \begin{equation}
    P \big[ P \ket{\psi} \big] = P \big[ \lambda \ket{\psi} \big] = \lambda \big[ P \ket{\psi} \big] = \lambda^2 \ket{\psi}.
    \end{equation}
    By using [Property 1](#property_1_of_Pauli_Strings) it can also be seen that
    \begin{equation}
    P \big[ P \ket{\psi} \big] = P^2 \ket{\psi} = \ket{\psi}.
    \end{equation}
    Therefore, 
    \begin{equation}
    \lambda^2 \ket{\psi} = \ket{\psi},
    \end{equation}
    meaning $\lambda = \pm 1$. Hence, the eigenvalues of any Hermitian element of the Pauli-group are $+1$ or $-1$.

    Now, using [Property 4](#property_4_Pauli_strings), it can be seen that the sum of the eigenvalues of any Pauli-group element is zero (as the trace of a square operator is the sum of its eigenvalues). As each of the eigenvalues can only be $-1$ or $-1$, there must be an equal number of eigenvectors that have eigenvalue $+1$ and there are with eigenvalue $-1$. Therefore, there are $2^{n-1}$ eigenvalues of $+1$ and $2^{n-1}$ eigenvalues of $-1$, as $\textrm{dim}~P=2^n$ meaning it has $2^n$ total eigenvalues.  

    Then, as $P$ is Hermitian, each of its eigenvectors are orthonormal. Hence, the $+1$ eigenspace of $P$ is spanned by $2^{n-1}$ orthogonal vectors, and is therefore of dimension $2^{n-1}$. The same argument can be made for the $-1$ eigenspace.   

    Now, let $P$ be a anti-Hermitian element of $\mathcal{P}_n$.

    As $P^2=-\mathbb{I}$ now, following the same proof as above it can be seen that the eigenvalues of $P$ will be $\pm i$. 

    We now note that any anti-Hermitian element of $\mathcal{P}_n$ can be written as 
    \begin{equation}
    P=\beta P_H,
    \end{equation}
    where $\beta = \pm i$ and $P_H$ is a Hermitian Pauli-group element. The rest of the above proof then applies, with the eigenvectors of $P$ and $P_H$ being the same,  completing the proof. 

    :::

7. Given any two Pauli-strings, $P_k, P_l \in \mathcal{P}^s_n$, it holds that
    \begin{equation}
    \textrm{tr}\big[P_k P_l \big] = 
    \begin{cases} 
    2^n  &\textrm{if} ~ k=l \\
    0    &\textrm{if} ~ k \neq l
    \end{cases}
    \end{equation}
    :::{dropdown} Proof
    
    It can be seen that 
    \begin{align*}
      P_kP_l &= P^1_k P_l^1 \otimes P^2_k P_l^2 \otimes \ldots \otimes P^n_k P_l^n \\
    \end{align*}
    where $P_q^\alpha$ is the single qubit Pauli operator of the $P_q~$th element of $\mathcal{P}_n$ at position $\alpha$.

    It is then noted that 
    \begin{equation}
    P_k^iP_l^i = \mathbb{I} \iff  P_k^i=P_l^i,
    \end{equation}
    as per [](#single_qubit_pauli_multiplication). Hence, 
    \begin{equation}
    P_kP_l = \mathbb{I} \iff P_k^i=P_l^i~\forall~i \in [1, n].
    \end{equation}

    If $P_k^i=P_l^i~\forall~i \in [1, n]$ then $P_k=P_l$, meaning that 
    \begin{equation}
    \textrm{tr}\big[P_k P_l \big] = \textrm{tr}\big[ \mathbb{I} \big] = d ~ ~ ~\textrm{if} ~ ~ ~ k=l.
    \end{equation} 

    If $P_k \neq P_l$, there exists at least one $i$ such that $P_k^i \neq P_l^i$, meaning that 
    \begin{equation}
    P_k P_l \neq \mathbb{I}. 
    \end{equation}
    Hence, using [Property 4](#property_4_Pauli_strings), it can be concluded that 
    \begin{equation}
    \textrm{tr} \big[ P_k P_l \big] = 0 ~ ~ ~ \textrm{if} ~ ~ ~ k \neq l,
    \end{equation}

    completing the proof.
    :::

8. The set $\mathcal{P}^s_n$ forms a complete basis for the space of $2^n \times 2^n$ complex matrices. 
    :::{dropdown} Proof
    
    We first consider the space of $2 \times 2 $ complex matrices. 

    An arbitrary $2 \times 2$ complex matrix is of the form 
    \begin{equation}
    A = \begin{bmatrix} a & b \\
    c & d 
    \end{bmatrix} ~ ~ \textrm{where} ~ ~ a,b,c,d \in \mathbb{C}.
    \end{equation}
    Now, let 
    \begin{align*}
    B &= \alpha \mathbb{I} + \beta X + \gamma Y + \delta Z, \\
    &= \begin{bmatrix} \alpha + \delta  & \beta - i \gamma \\
    \beta + i \gamma & \alpha - \delta 
    \end{bmatrix}
    \end{align*}
    where $\mathbb{I}$ is the qubit identity and $X, Y, Z$ are the [single qubit Pauli-operators](#single_qubit_pauli_operators_target).

    For $A=B$ it must be the case that 
    \begin{align*}
    \alpha &= \frac{a+d}{2} \\
    \beta &=  \frac{b+c}{2}            \\
    \gamma &=  \frac{c-b}{2i}   \\
    \delta &=  \frac{a-d}{2}              \\ 
    \end{align*}
    Therefore, for every combination of $a,b,c,d$ there exists a $\alpha, \beta, \gamma, \delta$ such that $A$ can be decomposed as a combination of the identity plus Pauli's. Therefore, the set $\{\mathbb{I}, X, Y, Z\}$ form an operator basis for the space of $2 \times 2$ complex matrices (for qubits). We note that, in general, $\alpha, \beta, \gamma, \delta \in \mathbb{C}$. 

    To expand to $2^n \times 2^n$ complex matrices, we first note that the space of operators on $\mathcal{H}^{2^n}$ is equilivent to the space of operators on $(\mathcal{H}^2)^{\otimes n}$, i.e., 
    \begin{equation}
    \mathcal{L}(\mathcal{H}^{2^n}) = \mathcal{L}(\mathcal{H}^2)^{\otimes n},
    \end{equation}
    where $\mathcal{L}(\mathcal{V})$ is the set of operators on the space $\mathcal{V}$. Therefore, if a basis of the space of operators on $(\mathcal{H}^2)^{\otimes n}$ can be found then it is also a basis of the space of operators on $\mathcal{H}^{2^n}$. 

    We then use the fact that in a tensor product space a basis of the whole space can be found by taking the tensor product of basis states from each subspace. See [here](#tensor_product_basis_target_basis_page) for a proof.  

    Hence, the set of operators 
    \begin{equation}
    \{\mathbb{I}, X, Y, Z\}^{\otimes n},
    \end{equation}
    i.e., the $n$-fold tensor product of all single qubit Pauli-operators, is basis of $\mathcal{H}^{2^n}$ — the $n$-qubit space. This set of operators is exactly $\mathcal{P}^s_n$ (the Pauli-strings), completing the proof.

    
    :::

(virtual_paulis_target_palui_group_page)=
### Virtual Paulis  

The generators of the $n$-qubit Pauli group given above act as single $X$ and $Z$ Pauli's on each physical qubit. There are $n$ $X$-type generators, and $n$ $Z$-type generators. 

One can also select a different sub-set of the $n$-Pauli-group to be generators of the group. This set can be choosen to represent _virtual_ $X$ and $Z$ type operators, in the sense that they will follow the expected commutation relations. For example, if
\begin{equation}
\mathcal{P}_n = \langle X'_j, Z_j', i \mathbb{I} \rangle_{j \in \{1,n\}},
\end{equation}
then 
(single_qubit_pauli_realtions)=
\begin{align*}
 [X'_j, X_k'] &= 0 ~\forall~j,k \in \{1,n\}, \\
 [Z'_j, Z_k'] &= 0 ~\forall~j,k \in \{1,n\}, \\
 [X'_j, Z_k'] &= 0 ~\forall~j,k \in \{1,n\}~{\rm if}~j \neq k, \\
 \{X'_j, Z_k'\} &= 0 ~\forall~j=k.
\end{align*}

The set $\{X_j, Z_j\}_{j \in \{1,n\}}$ is [ismorphic](#Isomorphism_definition_target_group_definitions) to $\{X'_j, Z'_j\}_{j \in \{1,n\}}$. 

Whilst each element of $\{X'_j, Z'_j\}_{j \in \{1,n\}}$ acts some single qubit Pauli operators on the physical qubits, they can be thought of as acting a single $X$ or $Z$ Pauli operator on one of $n$-virtual qubits. 

:::{dropdown} More Details
(more_detail_virtual_paulis_target)=
To see this, let the eigenbasis of the mutually commuting operators $\{Z'_j\}_{j \in \{1,n\}}$ be labeled by a bit-strings $\bm{b} = b_1b_2...b_n \in \{0,1\}^n$, such that 
\begin{equation}
Z'_j \ket{b_1b_2b_3 \ldots b_n} = (-1)^{b_j} \ket{b_1b_2b_3 \ldots b_n}.
\end{equation}
Hence, if the $j$th bit of $\bm{b}$ is $0$, then the basis state $\ket{\bm{b}}$ is in the positive eigenspace of the operator $Z'_j$. 

Consistency check: 
- For $n$ qubits, there are $2^n$ basis states to span the $2^n$ dimensional space. 
- Of the $2^n$ basis states, $2^{n-1}$ are in the postive eigenspace of $Z'_j$ and $2^{n-1}$ are in the negative eigenspace. 
- The eigenvalue of the product of operators $Z'_jZ'_k$ on $\ket{\bm{b}}$ is $(-1)^{b_j \oplus b_k}$, which is their individual eigenvalues mulitpled, as expected for commuting observables. 

The set of states $\big\{ \ket{\bm{b}} : b \in \{0,1\}^n \big\}$ can then be thought of as the computational basis states of the $n$-virtual qubits. 

Now, as $\{X'_j, Z_j'\}=0$, it holds that 
\begin{align*}
Z'_j  X'_j \ket{b_1b_2b_3 \ldots b_n}  &= -X'_j Z'_j \ket{b_1b_2b_3 \ldots b_n} \\
&= -(-1)^{b_j} X'_j \ket{b_1b_2b_3 \ldots b_n} \\
&= (-1)^{b_j \oplus 1} X'_j \ket{b_1b_2b_3 \ldots b_n} \\
&= X_j' Z_j' \ket{b_1b_2b_3 \ldots b_{j-1}(b_j \oplus 1)b_{j+1} \ldots b_n}.
\end{align*}
Therefore, 
\begin{align*}
X'_j \ket{b_1b_2b_3 \ldots b_n}  &= \ket{b_1b_2b_3 \ldots b_{j-1}(b_j \oplus 1)b_{j+1} \ldots b_n},
\end{align*}
meaning $X_j$ acts indepdently on the $j$th virtual qubit. Hence, in this basis, the virtual Pauli operators can be seen to act as single qubit Pauli-operators on each of the $n$ virtual qubits. 

The eigenvectors of $X_j'$ can be seen to be 
\begin{equation}
\frac{\ket{b_1b_2b_3 \ldots b_{j-1}b_jb_{j+1} \ldots b_n} + \ket{b_1b_2b_3 \ldots b_{j-1}(b_j \oplus 1)b_{j+1} \ldots b_n}}{\sqrt{2}}.
\end{equation}
:::