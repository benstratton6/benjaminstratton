---
title: Basis
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
keywords: Vectors, Vector Spaces, basis
abstract: The conditions for a set of vectors to be a basis and some properties of vector basis.  
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(basis_page_target)=
### Basis Conditions

Let $V$ be a vector space and $a_{1}, ~a_{2}, \ldots, ~a_{n}~\in~V~\forall~n$.  
(basis_basis_target)=
The set of vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ are a basis of $V$ if 
1. $\textrm{Span}(\{ a_{1}, ~a_{2}, \ldots ~a_{n} \}) = V$
    - Any vectors in $V$ can written as a linear combination of the vectors in $\{ a_{1}, ~a_{2}, \ldots ~a_{n} \} $ [💭](#span_definition_target). 
2. The vectors $\{ a_{1}, ~a_{2}, \ldots ~a_{n} \} $ are [linear independent](#linearly_independent_target_glossary).  

### Use of Basis

For any $\psi~\in~V$, if $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ forms a basis, there exists a unique set of scalars $\lambda_{1}, \lambda_2, \ldots, \lambda_{n}~\in~\mathbb{F}^{n}$ such that 
\begin{equation}
\psi = \lambda_{1} a_{1} + \lambda_2 a_{2} + \ldots + \lambda_{n} a_{n}.
\end{equation}
Hence, given a basis one can write any vector in the space as a sum over those vectors in the basis.  

#### Dimension Definition

The dimension of a vector space $V$ is the number of linearly independent vectors that span the space i.e., the dimension of a vector space is the number of vectors in any basis of the space. 

Therefore, if a vector space is known to be of dimension $n$, and it is spanned by $n$ vectors, those vectors must be linearly independent. 

### Basis Properties 

- All linear subspaces of a vector space have a basis. 
- All basis of a given subspace have the same number of elements.  

### Special Basis 

::::{tab-set}
:::{tab-item} Standard Basis
:sync: tab1
let $V$ be a vector space defined over $\mathbb{F}^{n}$.

The **standard basis** of a vector space $V$ is given by 
(standard_basis_basis_target)=
\begin{equation}
e_{1} &= \begin{bmatrix}
           1 \\
           0 \\
           \vdots \\
           0
         \end{bmatrix}, ~ ~ 
e_2 &= \begin{bmatrix}
0 \\
1 \\
\vdots \\
0
\end{bmatrix}, ~~ 
e_n &= \begin{bmatrix}
    0 \\
    0 \\
    \vdots \\
    1
    \end{bmatrix}.
\end{equation}

:::
:::{tab-item} Orthonormal Basis 
:sync: tab2
(Orthonormal_Basis_basis_target)=
Let the set of vectors $\{ a_{1}, ~a_{2}, \ldots, ~a_{n} \} $ be a basis of a vector space $V$. This basis is an orthonormal basis if 
\begin{equation}
a_{i} \cdot a_{j} = \delta_{ij},
\end{equation}
where $\delta_{ij}$ is the [Kronecker delta function](https://en.wikipedia.org/wiki/Kronecker_delta) given by 
\begin{equation}
\delta_{ij} \coloneqq \left\{
	\begin{array}{ll}
		1  & \mbox{if } i = j \\
		0 & \mbox{if } i \neq j
	\end{array}
\right.
\end{equation}
:::
::::
(tensor_product_basis_target_basis_page)=
### Tensor Product Basis 

Let the set of vectors $\{ a_i \}_i$ be a basis of the space $A$ and the set of vectors $\{ b_j \}_j$ be a basis of the space $B$.

The set of vectors $\{ a_i \otimes b_j\}_{i,j}$ is then a basis of the space $A \otimes B$, where $\otimes$ is the [tensor product](https://en.wikipedia.org/wiki/Tensor_product). 

:::{dropdown} Proof

A general element of the space $A \otimes B$, denoted $U$, is 
\begin{equation}
U = \sum_k c_k v^k \otimes u^k,
\end{equation} 
where 
\begin{equation}
c_k \in \mathbb{C}, ~ ~  v^k \in A, ~ ~ u^k \in B ~ ~\forall~k.
\end{equation}
Given $v_k \in A$ and the fact that $\{ a_i \}_i$ is a basis for $A$, there exists a set of complex coefficients $\{\alpha^k_i : \alpha^k_i \in \mathbb{C} \}_i$ such that 
\begin{equation}
v^k = \sum_i \alpha^k_i a_i.
\end{equation}
The same holds for $u^k \in B$ i.e., 
\begin{equation}
u^k = \sum_i \beta^k_i b_i,
\end{equation}
where $\{\beta^k_i : \beta^k_i \in \mathbb{C} \}_i$ is a set of complex coefficients. 

Hence, $U$ can be decomposed as 
\begin{align*}
U &= \sum_k \sum_i \sum_j c_k \alpha^k_i \beta^k_j a_i \otimes b_j \\
&= \sum_i \sum_j \kappa_{i,j} a_i \otimes b_j,
\end{align*}
where $\kappa_{i,j} = \sum_k c_k \alpha^k_i \beta^k_j$. Therefore, any arbitrary vector in $A \otimes B$ can be decomposed in terms of $\{ a_i \otimes b_j\}_{i,j}$. 

This shows that $\{ a_i \otimes b_j\}_{i,j}$ spans the space $A \otimes B$. 

To be a basis, the vectors $\{ a_i \otimes b_j\}_{i,j}$ must also be linearly independent. It can be seen that this must be the case, as 
\begin{equation}
\textrm{dim}(A \otimes B) = \textrm{dim}(A) \times \textrm{dim}(B).
\end{equation}
Then, as 
\begin{equation}
\textrm{dim}(A) = \vert \{ a_i \}_i \vert, ~ ~ \textrm{dim}(B) = \vert \{ b_i \}_i \vert,
\end{equation}
it is the case that 
\begin{equation}
\vert \{ a_i \otimes b_j \}_{i,j} \vert = \textrm{dim}(A \otimes B).
\end{equation}
Hence, the set of vectors $\{ a_i \otimes b_j \}_{i,j}$ span the space and the number of them is equal to the dimension of $A \otimes B$, hence they must be linearly independent and therefore form a basis of $A \otimes B$. 
:::
