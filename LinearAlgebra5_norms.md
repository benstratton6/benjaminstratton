---
title: Norms 
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
keywords: Norms, Vector Spaces, Vectors, Matrices 
abstract: The conditions for a [functional](#functional_target_glossary) on a vector space to be a norm and some examples of both vector and matrix norms.  
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(norms_page_target)=
## Norm Conditions

Let $V$ be a vector space over the field $\mathbb{F}$. A functional, $ \vert \vert \cdot \vert \vert $, on $V$ from it's elements to the positive real numbers, $\vert \vert \cdot \vert \vert: V \rightarrow \mathbb{R}^{+}$ is a norm if it satisfies the following conditions for $\psi, \sigma ~\in ~V$ and $\lambda~\in~\mathbb{F}^{1}$:

1. $\vert \vert \psi \vert \vert \geq 0$ where $\vert \vert \psi \vert \vert=0$ iif $\psi = 0$
    - Positivity 
2. $\vert \vert \lambda \psi \vert \vert = \vert \lambda \vert ~ \vert \vert \psi \vert \vert$
    - Scaling 
3. $\vert \vert \psi + \sigma \vert \vert \leq \vert \vert \psi \vert \vert + \vert \vert \sigma \vert \vert $
    - Triangle Inequality 
    - From this is can be seen that: $\vert ~ \vert \vert \psi \vert \vert - \vert \vert \sigma \vert \vert ~\vert \leq \vert \vert \psi - \sigma \vert \vert$

Norms can be thought of as functionals that measure the size of an elements of a vector space. A vector space with a norm is called a normed vector space. 

## Vector Norm Examples

::::{tab-set}
:::{tab-item} l_p-norm
:sync: tab1
Let $\psi~\in~V$ be a vector such that $\psi~\in~\mathbb{F}^{n}$ with elements $(\psi_1, \psi_2, \ldots, \psi_n)$. The $l_{p}$-norm is given by 
(L2_norm_norms_target)=
\begin{equation}
\vert \vert \psi \vert \vert_{p} = \big( \vert \psi_1 \vert^p + \vert \psi_2 \vert^p + \ldots + \vert \psi_n \vert^p)^{1/p}
\end{equation}
With $p=1$ and $p=2$ being the $1$-norm and Euclidean ($l_2$) Norm:
(l2_norm_norms_page_target)=
\begin{align*}
\vert \vert \psi \vert \vert_{1} &= \big( \vert \psi_1 \vert + \vert \psi_2 \vert + \ldots + \vert \psi_n \vert) \\
\vert \vert \psi \vert \vert_{2} &= \big( \vert \psi_1 \vert^2 + \vert \psi_2 \vert^2 + \ldots + \vert \psi_n \vert^2)^{1/2}
\end{align*}
:::
:::{tab-item} Sup-norm
:sync: tab2
Let $\psi~\in~V$ be a vector such that $\psi~\in~\mathbb{F}^{n}$ with elements $(\psi_1, \psi_2, \ldots, \psi_n)$. The Sup-norm is given by 
\begin{equation}
\vert \vert \psi \vert \vert_{\infty} = \max \{\vert \psi_i \vert~: 1 \leq i \leq n \}.
\end{equation}
This is just the maximum elements of $ \psi $. 
:::
::::

## Matrix Norms
In addition to satisfying the above requirements, to be considered a norm on a vector space, $M$, which has matrices as elements, the functional $\Omega: M \rightarrow \mathbb{R}^{+}$ must satisfy the following condition for all $A,B~\in~M$: 

1. $\vert \vert AB \vert \vert \leq \vert \vert A \vert \vert ~ \vert \vert B \vert \vert$

### Matrix Norm Examples

The following norms depend only on the singular values of the matrices they act upon. This means that the following conditions are true:
\begin{align*}
\vert \vert A \vert \vert = \vert \vert A V \vert \vert = \vert \vert U A  \vert \vert 
\end{align*}
where $V$ and $U$ are unitary matrices. 

Hence, these norms are all also unitarily invariant, meaning $\vert \vert A \vert \vert =  \vert \vert UAU^{\dagger} \vert \vert$. 

:::{dropdown} Proof

The singular valued decomposition of a matrix $A~\in~\mathbb{M}_{nm}(\mathbb{C})$ is 
\begin{equation}
A = U D V^{\dagger},
\end{equation}
where $U$ is an $m \times m$ complex unitary matrix, $V$ is a $n \times n$ complex unitary matrix, and $D$ is an $m \times n$ diagonal matrix with non-negative real numbers on the diagonal. These non-negative real numbers are the singular values of $A$. 

Consider a norm $\vert \vert \cdot \vert \vert: \mathbb{M}_{nm}(\mathbb{C}) \rightarrow \mathbb{R}^+$ that depends only on the singular values of the matrix it is applied to and let $W$ be a unitary operator. Consider now 
\begin{align*}
AW &= UDV^\dagger W, \\
&=  UD\tilde{V}^\dagger, 
\end{align*}
where $\tilde{V}^\dagger = V^\dagger W$ is just a different unitary matrix. Hence, it can be seen that the singular values of $A$ and $AW$ are the same - the non-negative real numbers on the diagonal of $D$ - and therefore that $ \vert \vert A W \vert \vert = \vert \vert A \vert \vert$. 

The same argument can be made to prove that $ \vert \vert W A \vert \vert = \vert \vert A \vert \vert$

A matrix $A \in \mathbb{M}_{nn}(\mathbb{C})$ has an [eigen-decomposition](https://mathworld.wolfram.com/EigenDecomposition.html) if 
\begin{align*}
A = Q P Q^\dagger
\end{align*}
where $Q$ has the eigenvectors of $A$ as it's columns and $P$ is a diagonal matrix with the eigenvalues of $A$ on it's diagonals. 

All matrices have a singular valued decompostion, but not all matrices have an eigen-decomposition. Moreover, unlike the singular values, the eigenvalues can be negative and complex. 

For [Hermitian](#hermitian_adjoint_page_target) matrices, the singular values are the absolute values of the eigenvalues. 

:::

Note, for [Hermitian](#hermitian_adjoint_page_target) matrices, the singular values are the absolute values of the eigenvalues. 

::::{tab-set}
:::{tab-item} Trace Norm
:sync: tab3

Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{M}_{mn}(\mathbb{F})$. The trace norm is given by
(trace_norm_target_norms)=
\begin{equation}
\vert \vert A \vert \vert_{\textrm{tr}} = \sum_{i} \mu_{i}(A),
\end{equation}
where $\mu_{i}(A)$ are the singular value of $A$. Hence, the Trace norm of $A$ is the sum of singular values of A. 

It is also given by 
\begin{equation}
\vert \vert A \vert \vert_{\textrm{tr}} = \textrm{tr} \big( \sqrt{A^{\dagger}A} \big). 
\end{equation}


:::
:::{tab-item} Frobenius Norm 
:sync: tab4
Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{M}_{mn}(\mathbb{F})$. The Frobenius norm is given by
(target_Frobenius_Norm_target)=
\begin{equation}
\vert \vert A \vert \vert_{F} = \sqrt{ \sum_{j}^{n} \sum_{i}^{m} \vert a_{ij} \vert ^{2} }.
\end{equation}

It is also given by 
\begin{equation}
\vert \vert A \vert \vert_{F} = \sqrt{\textrm{tr}(A^{\dagger}A)}. 
\end{equation}

:::
:::{tab-item} l_2 norm 
:sync: tab5
Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{M}_{mn}(\mathbb{F})$. Let $\psi~\in~V$ be a vector such that $\psi~\in~\mathbb{M}_{mn}(\mathbb{F})$ with elements $(\psi_1, \psi_2, \ldots, \psi_n)$.

The $l_2$ vector norm is given by 
\begin{equation}
\vert \vert \psi \vert \vert_{2} &= \big( \vert \psi_1 \vert^2 + \vert \psi_2 \vert^2 + \ldots + \vert \psi_n \vert^2)^{1/2}
\end{equation}

The $l_2$ norm of a matrix (also called the spectral norm) is given by the induced norm ([operator norm](#operator_norm_target_norms)) of the $l_2$ norm on a vector, 
(ltwo_norm_target_norms)=
\begin{equation}
\vert \vert A \vert \vert_2 = \sup_{\psi} \frac{ \vert \vert A \psi \vert \vert_2 }{ \vert \vert \psi \vert \vert_{2}}
\end{equation}

It is also given by 
\begin{equation}
\vert \vert A \vert \vert_2 = \sqrt{\mu_{\textrm{max}}(A^{\dagger}A)}
\end{equation}

:::
:::{tab-item} Ky Fan Norm
:sync: tab6
Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{M}_{mn}(\mathbb{F})$. The $k$-Ky Fan norm is given by
\begin{equation}
\vert \vert A \vert \vert^{k} _{*} = \sum_{i}^{k} \vert \mu^{\downarrow}_{i}(A) \vert,
\end{equation}
where $\mu^{\downarrow}_i (A)$ is the $i$th singular value of $A$ such that $ \mu^{\downarrow}_i(A) \geq \mu^{\downarrow}_{i+1}(A)~\forall~i$. Hence the Ky Fan Norm is the sum of the $k$th largest singular values.

**Ky Fan Dominance**: Let $B~\in~M$ be a matrix such that $B~\in~\mathbb{M}_{mn}(\mathbb{F})$. If it follows that
\begin{equation}
\vert \vert A \vert \vert^{k} _{*} \leq \vert \vert B \vert \vert^{k} _{*},
\end{equation}
for all $k$, then for all unitarily invariant norms it is the case that 
\begin{equation}
\vert \vert A \vert \vert \leq \vert \vert B \vert \vert.
\end{equation}
:::
:::{tab-item} Schatten Norms
:sync: tab7
Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{M}_{mn}(\mathbb{F})$. The Schatten norms are given by
(schatten_norms_target_norms_page)=
\begin{equation}
\vert \vert A \vert \vert_{p} = \bigg( \sum_{i}^{k} \big[\mu_{i}(A)\big]^{p} \bigg)^{\frac{1}{p}},
\end{equation}
where $\mu_i(A)$ are the singular values of $A$. 

Equally, Schatten norms can be written as 
\begin{equation}
\vert \vert A \vert \vert_{p} = \textrm{tr} \big[ \vert A \vert ^{p} \big]^{\frac{1}{p}},
\end{equation}
where $\vert A \vert = \sqrt{AA^{\dagger}}$. 

If $p=1$ you get the [trace norm](#trace_norm_target_norms), if $p=2$ you get the [Frobenius Norm](#target_Frobenius_Norm_target) and if $p=\infty$ you get the [$l_{2}$ norm](#ltwo_norm_target_norms). 
:::
::::

The following norms do not necessarily depend on the singular values and hence the above conditions might not hold. 

::::{tab-set}
:::{tab-item} Operator Norm
:sync: tab8
(operator_norm_target_norms)=
This is an induced norm. 

Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{F}^{m \times n}$. If $A$ is a linear map such that $A: V \rightarrow W$, where $V$ is a vector space over $\mathbb{F}^{m}$ and $W$ is a vector space over $\mathbb{F}^{n}$ then the operator norm is given by 
\begin{equation}
\vert \vert A \vert \vert_{op} = \inf \{c \geq 0: \vert \vert A \psi \vert \vert_{W} \leq c \vert \vert \psi \vert \vert_{V}~\forall~\psi~\in~V \},
\end{equation}
where $\vert \vert \cdot \vert \vert_{W}$ and $\vert \vert \cdot \vert \vert_{V}$ are vector norms on $V$ and $W$ respectively. 

The operator norm can be colloquially thought of as the maximum amount a map $A$ can lengthen a vector in $V$. 
:::
:::{tab-item} L_pq Norms
:sync: tab9
Let $A~\in~M$ be a matrix such that $A~\in~\mathbb{F}^{m \times n}$. The $L_{p,q}$ norm, where $p,q \geq 1$, is given by 
\begin{equation}
\vert \vert A \vert \vert_{p,q} = \biggl( \sum^{n}_{j} \bigg( \sum_{i}^{m} \vert a_{ij} \vert^{p} \bigg)^{\frac{q}{p}} \biggl)^{\frac{1}{q}},
\end{equation}
where $a_{ij}$ are the elements of $A$. 

The $L_{2,1}$ norm, which is the sum of the [$l_{2}$ vector norms](#L2_norm_norms_target) of the columns of $A$, is given by 
\begin{equation}
\vert \vert A \vert \vert_{2,1} = \sum^{n}_{j} \vert \vert a_j \vert \vert_{2} = \sum^{n}_{j} \bigg( \sum_{i}^{m} \vert a_{ij} \vert^{2} \bigg)^{\frac{1}{2}}
\end{equation} 
where $a_{j}$ are the columns of the matrix $A$. 
:::
::::

## Cross Norms

Consider a tensor product space $V = \mathcal{X} \otimes \mathcal{Y}$. 

A norm, $ \vert \vert \cdot \vert \vert $, is a cross norm if 
\begin{equation}
\vert \vert V \vert \vert = \vert \vert \mathcal{X} \otimes \mathcal{Y} \vert \vert = \vert \vert \mathcal{X} \vert \vert ~ \vert \vert \mathcal{Y} \vert \vert.
\end{equation}

All norms that depend only on the singular values are cross norms. 

:::{dropdown} Proof


**Note**: this is a somewhat *hand-wavey* proof.

Let the singular valued decomposition of a matrix $A~\in~\mathbb{M}_{nm}(\mathbb{C})$ be
\begin{equation}
A = U D_A V^{\dagger},
\end{equation}
and the singular valued decomposition of a matrix $B~\in~\mathbb{M}_{nm}(\mathbb{C})$ be
\begin{equation}
B = W D_B T^{\dagger}.
\end{equation}

Hence, the singular values of $A \otimes B$ are the product all of the singular values of $A$ with the singular values of $B$. 

The singular valued decomposition of a matrix $A \otimes B$ can then be seen to be 
\begin{align*}
A \otimes B = (U \otimes W)(D_A \otimes D_B)(V \otimes T)^\dagger.
\end{align*}

By observing this fact, it can be seen that any norms that depends only the singular values of a matrix can be factorised into a product of the norm applied to $A$ and $B$ separately. 


:::

## Useful Norm Inequalities 

::::{tab-set}
:::{tab-item} Hölder's Inequality 
:sync: tab1

Let $\mathcal{H}$ be a [Hilbert space](#hilbert_space_target), and let $ A, B \in \mathcal{H}$ be operators on the space. 

The following inequality:
\begin{equation}
\vert \vert AB \vert \vert_r \leq \vert \vert A \vert \vert_p ~ \vert \vert B \vert \vert_q, 
\end{equation}
where $\frac{1}{p} + \frac{1}{q} = \frac{1}{r}$. 

Note, Hölder's Inequality is more general than this, and applies to vector spaces other than Hilbert spaces and objects other than operators. See [here](https://mathoverflow.net/questions/158881/h%C3%B6lders-inequality-for-matrices) for some details

:::
:::{tab-item} Rastegin
:sync: tab2

Let $A \in \mathcal{H}_1 \otimes \mathcal{H}_2$ be an operator acting on the bipartite Hilbert space $\mathcal{H}$, and $\vert \vert \cdot \vert \vert_p $ be the [Schatten norm](#schatten_norms_target_norms_page), then: 
\begin{equation}
\vert \vert ~ \textrm{tr}_1 [ A ] ~ \vert \vert_p \leq \big[ {\rm dim}(\mathcal{H}_1)]^{(p-1)/p} \vert \vert A \vert \vert_p.
\end{equation}

The result it more general than this and more details can be found [here](
https://doi.org/10.48550/arXiv.1202.3853)

:::
:::{tab-item} Cauchy–Schwarz Inequality
:sync: tab3

Let $\bm{x}, \bm{y}~\in~V$, where $V$ is a [inner product space](#inner_product_space_definition_target) defined over $\mathbb{F}$ with inner product $(\cdot, \cdot) \rightarrow \mathbb{F}^{1}$, then 
\begin{equation}
\vert (\bm{x}, \bm{y}) \vert ^{2} \leq \vert \vert \bm{x} \vert \vert ~ \vert \vert \bm{y}  \vert \vert, 
\end{equation}
where $\vert \cdot \vert$ is the absolute value and 
\begin{equation}
\vert \vert \bm{x} \vert \vert = \sqrt{ (\bm{x}, \bm{x}) }.
\end{equation}  




::::


## Dual Norms

Consider a normed vector space $V$, where the norm is $\vert \vert \cdot \vert \vert$. 

There also exists norms on the [dual space](#dual_vector_spaces_target) of $V$, denoted $V^*$, which is the space of linear functionals on $V$. One method of finding norms on the dual space is to use norms of the primal space. These so called dual-norms are defined as 
\begin{equation}
\vert \vert f \vert \vert^* \coloneqq \sup_{X} \big\{ \vert f(X) \vert : \vert \vert X \vert \vert \leq 1, ~ ~ X \in V \big\},
\end{equation}
where $f \in V^*$ and $X \in V$. Intuitively, this can be understood as finding the $X$ within the unit-ball for which the functional $f$ maximally increases. 

These norms can be written in terms of only the primal vector space $V$ using the Riesz Representation Theorem. 
```{card} 
:header: [**Riesz Representation Theorem**](https://en.wikipedia.org/wiki/Riesz_representation_theorem#Riesz_representation_theorem)

Consider a finite dimension vector space $V$, with an [inner product](#inner_product_space_definition_target), denoted by $(\cdot, \cdot)$, that is linear in the first argument and anti-linear in the second argument. 

The **Riesz Representation Theorem** then states that for all linear functionals $f \in V^*$ there exists a unique vector $Y \in V$ such that 
\begin{equation}
f(X) = (X, Y), ~ ~ X \in V.
\end{equation} 
```
Using the Riesz Representation Theorem, one can identify each linear functional $f \in V^*$ via a $Y \in V$. The dual norms are then typically written as 
\begin{equation}
\vert \vert Y \vert \vert^* \coloneqq \sup_{X} \big\{ \vert (X,Y) \vert : \vert \vert X \vert \vert \leq 1, ~ ~ X \in V \big\},
\end{equation}
where $f(X) = (X,Y)$ and the $Y$ whilst in $V$ represents an elements of $V^*$. 

For the inner product $(X,Y) = \textrm{tr} \big[ X^\dagger Y \big]$, for example, the dual norm is 
\begin{equation}
\vert \vert Y \vert \vert^* \coloneqq \sup_{X} \big\{ \vert \textrm{tr} \big[ X^\dagger Y \big] \vert : \vert \vert X \vert \vert \leq 1, ~ ~ X \in V \big\}.
\end{equation}

### Dual Norm Examples

::::{tab-set}
:::{tab-item} Trace Norm Dual 
:sync: tab1

The dual of the trace norm (one norm), $\vert \vert A \vert \vert_1$, is 
\begin{equation}
\vert \vert A \vert \vert_1^* = \vert \vert A \vert \vert_{\infty},
\end{equation}
such that the dual norm of the trace norm is the infinity norm.

:::
:::{tab-item} Infinity Norm Example
:sync: tab2


The dual of the infinity norm (operator norm), $\vert \vert A \vert \vert_{\infty}$, is 
\begin{equation}
\vert \vert A \vert \vert_{\infty}^* = \vert \vert A \vert \vert_{1}
\end{equation}
such that the dual norm of the infinity norm is the trace norm.

::::

Note, some norms as self dual, meaning the dual of the norm returns the same norm. 

### The Dual of a Dual

The dual of a dual norm returns the original norm. 

This can be used to give alternative ways to phrase the original norm. For example, the dual of the trace norm is defined as 
\begin{equation}
\vert \vert Y \vert \vert_{\rm tr}^* \coloneqq \sup_{X} \big\{ \vert (X,Y) \vert : \vert \vert X \vert \vert_{\rm tr} \leq 1, ~ ~ X \in V \big\}.
\end{equation}
Now, the dual of $\vert \vert Y \vert \vert_{\rm tr}^*$ is defined as
\begin{equation}
\big[ \vert \vert Y \vert \vert_{\rm tr}^* \big]^* \coloneqq \sup_{X} \big\{ \vert (X,Y) \vert : \vert \vert X \vert \vert_{\rm tr}^* \leq 1, ~ ~ X \in V \big\}.
\end{equation}
But, the dual of the dual is the original norm, such that 
\begin{equation}
\big[ \vert \vert Y \vert \vert_{\rm tr}^* \big]^* = \vert \vert Y \vert \vert_{\rm tr}.
\end{equation}
It was then shown in the examples above that the dual of the trace norm is the infinity norm. Hence, an equivalent form for the trace norm is 
\begin{equation}
\vert \vert Y \vert \vert_{\rm tr} \coloneqq \sup_{X} \big\{ \vert (X,Y) \vert : \vert \vert X \vert \vert_{\infty} \leq 1, ~ ~ X \in V \big\}.
\end{equation}