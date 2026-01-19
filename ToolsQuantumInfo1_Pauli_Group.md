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

### Group Properties