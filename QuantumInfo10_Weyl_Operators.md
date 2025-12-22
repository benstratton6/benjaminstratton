---
title: Discrete Weyl Operators
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
keywords: Weyl Operators, Complete Basis.   
abstract: Details, properties and applications of the discrete Weyl operators   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

The discrete Weyl operators are a set of unitary operators that form a complete basis for the space of complex matrices. Within quantum information, they are used to define discrete Wigner functions [](https://doi.org/10.1016/0003-4916(87)90176-X), study non-stabilizerness [](10.1088/1367-2630/16/1/013009), and define basis of bipartite maximally entangled states, among other things. 

## Definition

The discrete Weyl operators are defined as 
\begin{equation}
    W_{a,b} = X^a Z^b, \hspace{2mm}  a,b \in \{0, 1, ~... ~,d-1\},
\end{equation}
where 
\begin{equation}
    X = \sum_{j=0}^{d-1} \vert j+1  ~ \textrm{mod} ~d \rangle \langle j \vert, ~ ~ Z= \sum_{j=0}^{d-1} \Omega^j \vert j \rangle \langle \vert, ~ ~ \Omega = e^{\frac{2 \pi i}{d}},
\end{equation}
such that the $(a,b)$th discrete Weyl operator is 
\begin{equation}
    W_{a,b} = \sum_{c} \Omega^{bc} \ket{c + a ~ \textrm{mod} ~d}\bra{c}.
\end{equation}
The $X$ and $Z$ in the definition of the discrete Weyl operators can be thought of as generalised Pauli-operators in higher dimensional spaces. They are also referred to as shift and clock operators. We note that for qubit systems, the discrete Weyl operators are
\begin{equation}
    W_{0,0} = \mathbb{I}, ~ ~ W_{0,1} = \sigma_z, ~ ~ W_{1,0} = \sigma_x, ~ ~ W_{1,1} = -i \sigma_y,
\end{equation}
where $\sigma_x, \sigma_y, \sigma_z$ are the qubit $X, Y$ and $Z$ Pauli-operators respectively. 

### Identities 

Here we list some identities for the Weyl operators.  

```{card} 
:header: **Transposition, Adjoint, and Multiplication**
:footer: 

The following identities are for how the discrete Weyl operators are transformed via transposition, adjoint, and multiplication:
\begin{equation}
    \begin{split}
        (W_{a, b}) ^ {t} &= \Omega^{-ab}W_{-a, b}, \\
        (W_{a, b}) ^ {\dagger} &= \Omega^{ab}W_{-a, -b}, \\
        W_{a, b}W_{c, d} &= \Omega^{bc}W_{a + c, b + d} = \Omega^{bc - ad}W_{c, d}W_{a, b}. \\ \label{weylIdentites}
    \end{split}
\end{equation}

```

```{card} 
:header: **Trace and Inner Product**
:footer: 

The following identities are for the trace and (Hilbert-Schmidt) inner product of Weyl operators:
\begin{equation}
    \begin{split}
        \textrm{tr}\big[ W_{a,b} \big] &= d ~ \delta_{a,0} \delta_{b,0}, \\
        \textrm{tr}\big[ W_{a,b}^\dagger W_{c,d} \big] &= d ~ \delta_{a,c} \delta_{b,d},
    \end{split}
\end{equation}
where $\delta_{a,b}$ is the Kronecker delta function. 

```

### A Complete Operator Basis

The set 
\begin{equation}
    \bigg\{ \frac{1}{\sqrt{d}} W_{a,b} : a,b \in \{0, 1, ~... ~,d-1\} \bigg\},
\end{equation}
form a complete orthonormal basis for the space of $d \times d$ complex operators. 

Hence, if $A$ is a $d \times d$ complex operator there always exists a set of complex coefficients $p_{a,b} \in \mathbb{C}$ such that 
\begin{equation}
    A = \frac{1}{\sqrt{d}}\sum_{a,b=0}^{d-1} p_{a,b} W_{a,b}.
\end{equation}

### Generating A Maximally Entangled Basis

Let $\ket{\Phi^+_{00}} = d^{-1/2} \sum_{i=0}^{d-1} \ket{ii} \in \mathcal{H}^d$, meaning $\ket{\Phi^+_{00}}$ is a d-dimensional maximally entangled state. 

The following set is an orthonormal basis for the space $\mathcal{H}^d \otimes \mathcal{H}^d$:
\begin{equation}
    \big\{ \ket{\Phi_{a,b}^+} = (\mathbb{I} \otimes W_{a,b}) \ket{\Phi_{00}^+} ~  : ~ a,b \in \{0, 1, ~... ~,d-1\} \big\}
\end{equation}
We note that this holds for any basis of unitaries that are orthogonal under the Hilbert Schmit inner product.   