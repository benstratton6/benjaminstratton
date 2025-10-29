---
title: Inner Products 
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
keywords: Vectors, Vector Spaces, Inner Products. 
abstract: The conditions for a functional of two vectors to be an inner product. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(inner_product_space_definition_target)=
A [vector space](#vector_space_axioms_target), $V$, with an inner product is called an *inner product space*. 
(inner_product_definition_target)=
An inner product, $(\cdot, \cdot)$, is a functional that takes two vectors from the vector space $V$, defined over a field $\mathbb{F}^{n}$, as an input and outputs a scalar, $(\cdot, \cdot): \mathbb{F}^{n} \otimes \mathbb{F}^{n} \rightarrow \mathbb{F}^{1}$. 

## Inner Product Conditions

Let $\psi, ~\sigma ~\in~V$ and $a \in \mathbb{F}^{1}$.
(inner_product_target_definition_inner_product_space)=
To be an inner product the functional $(\cdot, \cdot)$ must obeys the following properties:

1. $(\psi, \psi) \geq 0$ and $(\psi, \psi) = 0$ if and only if $\psi=0$
    - Positive-definiteness
2. $(\psi,\omega) = (\omega, \psi)^{*}$
    - Conjugate symmetry
    - If $V$ is defined over $\mathbb{R}$ then $(\psi,\omega) = (\omega, \psi)$
3. $(a\psi, \omega) = a (\psi, \omega)$
    - Linearity in the first argument
    - If $V$ is defined over $\mathbb{C}$ then $(a \psi,\omega) = a^*(\psi, \omega)$
4. $(\omega + \sigma, \psi) = (\omega, \psi) + (\sigma, \psi)$
    - Additivity

## Implication

Given a vector space $V$ with an inner product as defined above, one finds that 
\begin{equation}
(\sigma, \psi + \omega) = (\sigma,\psi) + (\sigma, \omega), ~ ~ ~ (\psi, a\omega) = a^* (\psi, \omega)
\end{equation}
which is called being anti-linear in the second argument. Hence, linearity in the first argument implies anti-linearity in the second argument. 

:::{dropdown} Proof
\begin{align*}
(\psi, a\omega) &= (a \omega, \psi)^* \\
&= \big[a (\omega, \psi) \big]^* \\
&= a^* (\omega, \psi)^* \\
&= a^* (\psi, \omega)
\end{align*}
\begin{align*}
(\sigma, \psi + \omega) &= (\psi + \omega, \sigma)^*\\
&= \big[(\psi, \sigma)  + (\omega, \sigma) \big ]^* \\
&= (\psi, \sigma)^*  + (\omega, \sigma)^* \\\
&= (\sigma, \psi)  + (\sigma, \omega).
\end{align*}
:::

## Cauchy–Schwarz inequality

The Cauchy–Schwarz inequality is an upper bound on the inner product between two vectors, in any vector space, in terms of the [norms](#norms_page_target) of the vectors, where the norm is defined via the inner product.

Let $\bm{x}, \bm{y}~\in~V$, where $V$ is a inner product space defined over $\mathbb{F}$ with inner product $(\cdot, \cdot) \rightarrow \mathbb{F}^{1}$, then 
\begin{equation}
\vert (\bm{x}, \bm{y}) \vert ^{2} \leq \vert \vert \bm{x} \vert \vert ~ \vert \vert \bm{y}  \vert \vert, 
\end{equation}
where $\vert \cdot \vert$ is the absolute value and 
\begin{equation}
\vert \vert \bm{x} \vert \vert = \sqrt{ (\bm{x}, \bm{x}) }.
\end{equation}  
