---
title: Groups Definition 
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
keywords: Groups, Group Theory. 
abstract: A brief overview of discrete groups and some important group theory concepts. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

There is much literature on groups, these particular notes were made using [](https://doi.org/10.48550/arXiv.2605.29137) and only pertain to discrete groups.

## Group Definition

Consider a set $G$ and a [binary operation](#binary_operation_glossary) $* :  G \times G \rightarrow G$. Then $(G, *)$ is a group if the following conditions hold: 
(group_page_group_definition)=
1. $(a * b) * c = a * (b * c), ~ ~ a,b,c \in G$
    - Associativity 
2. $ \exists ~ e \in G$ such that $e * g = g * e~\forall~g \in G$
    - Unique identity element
3. $ \forall a \in G, ~ ~\exists~b \in G$ such that $a * b = b * a = e$.
    - Unique inverse element denoted as $a^{-1}$ for $a \in G$. 

## Abelian Groups

Let $(G, *)$ be a group. For $a,b \in G$, it is said that $a$ and $b$ commute if $a * b = b*a$. 
(albelian_group_definition)=
A group is said to be abelian if all elements of $G$ mutually commute. If not, it is said to be non-abelian. 

## Subgroups 
(group_page_subgroup_definition)=
Let $(G, *)$ be a group. Given a subset $H \subseteq G$, then $(H, *)$ is a subgroup of $(G, *)$ if $(H, *)$ is [group](#group_page_group_definition). 

## Group Generators
(group_generators_definition)=
The generators of a group $(G, *)$ are a subset of the elements of $G$ from which the whole set can be found via binary operations of the generators. 

Formally, for a group $(G, *)$, a subset $S \subseteq G$ is a generating set if every element in $G$ can be written as a finite product of elements in $S$ and their inverses. Mathematically, this can captured as
\begin{equation}
G = \langle S \rangle = \big\{ s_1^{\alpha_1}s_2^{\alpha_2}\ldots s_k^{\alpha_k} : k \geq 0, s_k \in S~\forall k, ~\alpha_k \in \mathbb{Z}~\forall ~k \big\}.
\end{equation}

(abelian_group_generators_target)=
```{card} 
:header: Abelian Group Generators

Let $G$ be an [abelian group](#albelian_group_definition) of self inverse elements with generators $S = \big\{s_1, s_2, \cdots, s_n \big\}$. Then, any element $g \in G$ can be written as
\begin{equation}
g = \prod_{i=1}^m g_i^{\alpha_i} ~ : ~ ~ \alpha_i \in \{0,1\}~\forall i.
\end{equation}
```

## Centralizer 

Let $(G, *)$ be a group and let $(H, *)$ be a [subgroup](#group_page_subgroup_definition) of $(G, *)$. 

The centralizer of $(H,*)$ in $(G, *)$ is 
(centralizer_definition_target)=
\begin{equation}
C_G(H) = \big\{ g \in G : g * h = h * g ~\forall~h \in H \big\},
\end{equation}
meaning that the centralizer contains all the elements of $G$ that commute with all the elements of $H$. 

### Centre 

Let $(G, *)$ be a group.

The centre of $(G, *)$ is 
(centre_definition_target)=
\begin{equation}
C(G) = \big\{ g \in G : g * h = h * g ~\forall~h \in G \big\},
\end{equation}
meaning that the centralizer contains all the elements of $G$ that commute with all the other elements of $G$. 

Note, $C(G) = C_G(G)$

## Normalizer 

Let $(G, *)$ be a group and let $(H, *)$ be a [subgroup](#group_page_subgroup_definition) of $(G, *)$. 

The normalizer of $(H,*)$ in $(G, *)$ is 
(normalizer_definition_target)=
\begin{equation}
N_G(H) = \big\{ g \in G : gHg^{-1} = H \big\} 
\end{equation}
where 
\begin{equation}
g H g^{-1} =  H \iff \big\{ g * h_i * g^{-1} : h_i \in H \big\} = H.
\end{equation} 
The normalizer is therefore all the elements of $G$ that map all the elements of $H$ back to itself under conjugation. 

In general the centralizer is contained within the normalizer,
\begin{equation}
C_G(H) \subseteq N_G(H),
\end{equation}
as commuting is a weaker condition than preserving under conjugation. 

## Group Examples

::::{tab-set}
:::{tab-item} Integers/addition 
:sync: tab1

Let $\mathbb{Z}$ be the set of all integers. Let $+$ be the binary operation of addition. Then $(\mathbb{Z}, +)$ is a group. 

:::
:::{tab-item} Invertible real matrices/multiplication
:sync: tab2

Let $\mathbb{M}_n$ be the set of $n \times n$ invertible matrices. Let $\times$ be the binary operator of [matrix multiplication](#traget_matrix_multiplication). Then $(\mathbb{M}_n, \times)$ is a group.  

:::
:::{tab-item} n-qubit Pauli Group
:sync: tab3

The elements of the $n$-qubit Pauli group $\mathcal{P}_n$ are the $n$-fold tensor product of single qubit Pauli-strings with all possible phases:
\begin{equation}
\mathcal{P}_n = \big\{ \mathbb{I}, X, Y, Z \big\}^{\otimes n} \times \{\pm 1, \pm i\}.
\end{equation}
The binary operator is then multiplication. 

See the [Pauli-group page](#Pauli_group_page_target) for more details.  

:::
::::



