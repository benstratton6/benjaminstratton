---
title: Vector Spaces
subject: Tutorial
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
keywords: Vectors, Vector Spaces
abstract: The conditions for a vector space. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(vector_space_page_target)=
A vector space, defined over a field $\mathbb{F}$, is a set $V$ whose elements can be added together and multiplied by a scalars ($\mathbb{F}^{1}$). The elements of $V$, whilst often called vectors, can be a variety of different mathematical objects, such as [vectors](#vector_example) in the typical sense, or matrices. 

Vector spaces defined over $\mathbb{R}$ are known as real vector spaces, whilst vector spaces defined over $\mathbb{C}$ are defined as complex vector spaces. 

### Vector Space Axioms
Let $\psi, ~\sigma, ~\omega~\in~V$ and $a,b \in \mathbb{F}^{1}$.

In order for $V$ to be a vector space, the addition and scalar multiplication operations must meet a set of Axioms, defined below.

The addition operation must obey the following conditions 
(vector_space_axioms_target)=
1. $~~\psi + \sigma = \sigma + \psi$
    - Commutativity
2. $\psi + (\sigma + \omega) = (\psi + \sigma) + \omega$
    - Associativity
3. $\exists ~I \in ~V$ such that $\psi + I = \psi$.
    - Identity
4. $~~\forall~v~\in~V, \exists -v~\in~V$ such that $v+-v=I$.
    - Inverse

The multiplication by a scalar operation must obey the following conditions 
1. $a(\psi + \omega) = a \psi + b \omega$
    - distributive over $V$
2. $(a+b)\psi = a\psi + b\psi$
    - distributive over scalar


### Further Vector Space Properties 
::::{tab-set}
:::{tab-item} Linear Combination
:sync: tab1
Let $a_{1}, ~a_{2}, \ldots ~a_{n}~\in~V~\forall~n$ and $\lambda_1,~\lambda_2, \ldots ~\lambda_n~\in~\mathbb{F}^{1} ~\forall~n$
(linear_combination_Vector_space_target)=
A linear combination of the vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ is given by

\begin{equation}
\tilde{a} = \lambda_1 a_{1} + \lambda_2 a_2 \ldots \lambda_n a_n
\end{equation}
All linear combinations of vectors in $V$ are also in V, $\tilde{a}~\in~V$. 
:::
:::{tab-item} Linear (In)dependence
:sync: tab2
Let $a_{1}, ~a_{2}, \ldots ~a_{n}~\in~V~\forall~n$ 

**linearly dependent:** The set of vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ are linearly dependent if there exists $\lambda_1,~\lambda_2, \ldots ~\lambda_n~\in~\mathbb{F}^{1}$, where $\lambda_{j}$ is not equal to $0$ for all $n$, such that 
\begin{equation}
\lambda_1 a_{1} + \lambda_2 a_2 \ldots \lambda_n a_n = 0
\end{equation}

(linearly_independent_target)=
**linearly independent:** The set of vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ are linearly independent if there does not exists $\lambda_1,~\lambda_2, \ldots ~\lambda_n~\in~\mathbb{F}^{1}$ such that 
\begin{equation}
\lambda_1 a_{1} + \lambda_2 a_2 \ldots \lambda_n a_n = 0
\end{equation}
unless $\lambda_{j}$ is equal to $0$ for all $n$.

In a space defined over $\mathbb{F}^{m}$, the most elements a set of linearly independent vectors could contain is $m$.  
:::
:::{tab-item} Linear Subspace
:sync: tab3
Let $G \subset V$ 

$G$ is a linear subspace of $V$ if 
1. $G \neq \varnothing$, 
    - the set $G$ is not empty 
2. $\forall~\psi, \sigma \in G$ it is true that $\psi + \sigma \in G$, 
    - $G$ is closed under addition.
3. $\forall~\psi,~~ \lambda \in \mathbb{F}^{1}$ it is true that $\lambda \psi \in G$, 
    - $G$ is closed under multiplication.
:::
:::{tab-item} Basis
:sync: tab4
Let $a_{1}, ~a_{2}, \ldots, ~a_{n}~\in~V~\forall~n$ 
(basis_vector_space_target)=
The set of vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ are a basis of $V$ if 
1. $\textrm{Span}(\{ a_{1}, ~a_{2}, \ldots ~a_{n} \}) = V$
    - Any vectors in $V$ can written as a linear combination of the vectors in $\{ a_{1}, ~a_{2}, \ldots ~a_{n} \} $ [💭](#span_definition_target). 
2. The vectors $\{ a_{1}, ~a_{2}, \ldots ~a_{n} \} $ are [linear independent](#linearly_independent_target_glossary).  

For any $\psi~\in~V$, if $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ forms a basis, there exists a unique set of scalars $\lambda_{1}, \lambda_2, \ldots, \lambda_{n}~\in~\mathbb{F}^{n}$ such that 
\begin{equation}
\psi = \lambda_{1} a_{1} + \lambda_2 a_{2} + \ldots + \lambda_{n} a_{n}.
\end{equation}

(dimension_vector_spaces_target)=
The **dimension of a vector space** $V$, given by $\textrm{dim}V$, is the minimum number of elements in a basis of $V$, or the number of vectors needed to Span $V$. 

For more on basis [see here](#basis_basis_target)
:::
::::

### Subspaces 
(vector_subspaces_definition_target)=
Let $V$ be a vector space over $\mathbb{F}$. A subset $U \subset V$ is a subspace of $V$ if the following conditions hold
1. $U \neq \emptyset$
    - The subset is not empty.
2. $u+v~\in~U~\forall~u,v~\in~U$.
    - $U$ is closed under addition.
3. $\lambda u~\in~U~\forall~u~\in~U, \lambda~\in~\mathbb{F}^{1}$ 
    - $U$ is closed under multiplication by scalars. 

### Properties and Operations of Subspaces

::::{tab-set}
:::{tab-item} Union of Subspaces
:sync: tab1
Let $V$ be a vector space and $U$ and $W$ be subsets of $V$, $U,W~\subset~V$. 

The union of $U$ and $W$ is also a subspace of $V$: 
\begin{equation}
U \cap W \subset V
\end{equation}
:::
:::{tab-item} Direct Sum
:sync: tab2

Let $V$ be a vector space and $U$ and $W$ be subsets of $V$, $~U,W~\subset~V$, such that $U \cap W = \{0\}$.

The direct sum of these subspace is given by
(direct_sum_vector_spaces)=
\begin{equation}
U \oplus W \coloneqq U + V \coloneqq \{u + w: u~\in~U, w~\in~W\}
\end{equation}

**Properties**

- All vectors in $U \oplus W$ can be decomposed into a vector in $U$ and a vector in $W$. 
- $\textrm{dim}(U \oplus W) = \textrm{dim}U + \textrm{dim}W$. 
::::





