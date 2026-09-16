---
title: Classical Linear Codes
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
keywords: bits, bit-flips, repetition code 
abstract: The mathematical formulation of a broad class of classical error correcting codes.
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

In this section, we will give a mathematical description of a broad class of binary classical error correcting codes called linear codes, which includes the [repetition code](#classical_error_correction_page) and [parity check codes](#section_parity_check_codes_target) introduced in the previous section. 

Three methods of representing a classical linear code will be given. For each, the [parity error detection](#error_detection_with_parity_example) and [correction](#error_correction_with_parity_example) examples will be detailed.  

Finally, in this section we will denoted an $n$ bit-strings as an $n$ dimensional vectors in the vector space $\mathbb{F}^n_2$, i.e,
\begin{equation}
a_1a_2 \ldots a_n \rightarrow \bm{a} = \begin{bmatrix}
           a_{1} \\
           a_{2} \\
           \vdots \\
           a_{n}
         \end{bmatrix} ~ ~ ~{\rm where} ~ ~a_i \in \mathbb{F}^1_2.
\end{equation} 

## Definition

A classical linear code is a [subspace](#vector_subspaces_definition_target) $\mathcal{C} \subseteq \mathbb{F}^n_2$. All of elements of $\mathcal{C}$ are the code words of the error correction code. 

As $\mathcal{C}$ is a subspace, it holds that for any $\bm{a}, \bm{b} \in \mathcal{C}$ that 
\begin{equation}
\bm{a} + \bm{b} \in \mathcal{C},
\end{equation}
where all addition is modulo $2$. Hence, the sum of any two code words is another code word.  

If $k$ logical bits are encoded, then ${\rm dim}(\mathcal{C})=k$. 

## Code Representation

### List Code Words 

The most obvious — but expensive — method for representing a code is to list all of its code words. 

***Examples***

:::{dropdown} [Error Detection With Parity](#error_detection_with_parity_example)
Logical bit-string $\rightarrow$ Code Word: 
\begin{align*}
&000 \rightarrow [0000]^t \\
&001 \rightarrow [0011]^t \\
&010 \rightarrow [0101]^t \\
&011 \rightarrow [0110]^t \\
&100 \rightarrow [1001]^t \\
&101 \rightarrow [1010]^t \\
&110 \rightarrow [1100]^t \\
&111 \rightarrow [1111]^t \\
\end{align*}

:::

:::{dropdown} [Error Correction With Parity](#error_correction_with_parity_example)
Logical bit-string $\rightarrow$ Code Word: 
\begin{align*}
&000 \rightarrow [000,000]^t \\
&001 \rightarrow [001,011]^t \\
&010 \rightarrow [010,101]^t \\
&011 \rightarrow [011,110]^t \\
&100 \rightarrow [100,110]^t \\
&101 \rightarrow [101,101]^t \\
&110 \rightarrow [110,011]^t \\
&111 \rightarrow [111,000]^t \\
\end{align*}

:::

### Generators

A set of vectors $\bm{u}_1, \bm{u}_2, \ldots, \bm{u}_m \in \mathcal{C}$ is said generate the code $\mathcal{C}$ if 
\begin{equation}
\mathcal{C} = \big\{ \alpha_1 \bm{u}_1 + \alpha_2 \bm{u}_2 + \ldots + \alpha_m \bm{u}_m : \alpha_i \in \mathbb{F}^1_2~\forall i \big\}
\end{equation}

If all $\bm{u}_1, \bm{u}_2, \ldots, \bm{u}_m \in \mathcal{C}$ are [linearly independent](#linearly_independent_target) then the set is called a minimal generating set. 

From this definition, it can be see that a minimal generating set of a code is a [basis](#basis_basis_target) for the subspace $\mathcal{C}$, meaning $m=k$. 

Consider now a code encoding $k$ logical bits into $n$ physical bits, such that $p=n-k$ parity bits are used for the error correction. Then, from a minimal generating set of a code (they are not unique), a generating matrix $G$ can be created as follows
(generating_matrix_target)=
\begin{equation}
G = \left[
\begin{array}{cc}
  \mathbb{I}_{k \times k} \\
  \hline
   A_{p \times k}
\end{array}
\right],
\end{equation}
such that $\mathbb{I}_{k \times k}$ is the $k \times k$ identity matrix and $A_{p \times k}$ is an $p \times k$ matrix that encodes which parity checks occur. 

If $\bm{x} \in \mathbb{F}^k_2$ is an unencoded bit-string, then its encoded bit-string $\bm{y} \in \mathcal{C} \subseteq \mathbb{F}^n_2$, which includes its parity bits, is given by
\begin{equation}
\bm{y} = G \bm{x},
\end{equation} 
hence the term generating matrix for $G$. 

***Examples***

:::{dropdown} [Error Detection With Parity](#error_detection_with_parity_example)

A minimum generating set for this code is given by the code-words 
\begin{align*}
&001 \rightarrow [0011]^t \\
&010 \rightarrow [0101]^t \\
&100 \rightarrow [1001]^t \\
\end{align*}
It can easily be see that for any arbitrary unencoded bit-string $a_1a_2a_3$ it follows that 
\begin{equation}
\begin{bmatrix}
           a_{1} \\
           a_{2} \\
           a_3 \\
           p(\bm{a})
         \end{bmatrix} = a_1 \begin{bmatrix}
           1 \\
           0 \\
           0 \\
           1
         \end{bmatrix} + a_2 \begin{bmatrix}
           0 \\
           1 \\
           0 \\
           1
         \end{bmatrix} +  a_3 \begin{bmatrix}
           0 \\
           0 \\
           1 \\
           1
         \end{bmatrix}
\end{equation}

The generating matrix is then 
\begin{equation}
G = \left[
\begin{array}{ccc}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
  \hline
 1 & 1 & 1
\end{array}
\right].
\end{equation}
:::

:::{dropdown} [Error Correction With Parity](#error_correction_with_parity_example)

A minimum generating set for this code is given by the code-words 
\begin{align*}
&001 \rightarrow [001,011]^t \\
&010 \rightarrow [010,101]^t \\
&100 \rightarrow [100,110]^t \\
\end{align*}
such that for any arbitrary unencoded bit-string $a_1a_2a_3$ it follows that 
\begin{equation}
\begin{bmatrix}
           a_{1} \\
           a_{2} \\
           a_3 \\
           a_1 \oplus a_2 \\
           a_1 \oplus a_3 \\
           a_2 \oplus a_3
         \end{bmatrix} = a_1 \begin{bmatrix}
           1 \\
           0 \\
           0 \\
           1 \\
           1 \\ 
           0
         \end{bmatrix} + a_2 \begin{bmatrix}
           0 \\
           1 \\
           0 \\
           1 \\ 
           0 \\
           1
         \end{bmatrix} +  a_3 \begin{bmatrix}
           0 \\
           0 \\
           1 \\
           0 \\
           1 \\
           1
         \end{bmatrix}
\end{equation}
The generating matrix is then 
\begin{equation}
G = \left[
\begin{array}{ccc}
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1 \\
  \hline
 1 & 1 & 0 \\
 1 & 0 & 1 \\
 0 & 1 & 1
\end{array}
\right].
\end{equation}
:::

### Parity Checks

Let $\bm{v}_1, \bm{v}_2, \ldots, \bm{v}_m \in \mathbb{F}^n_2$ represented a set of parity checks.  A codespace $\mathcal{C}$ can then be defined as
\begin{equation}
\mathcal{C} = \big\{ \bm{a} \in \mathbb{F}^n_2 : \bm{a} \cdot \bm{v}_i = 0 ~\forall~i  \big\}.
\end{equation}
In words, the code space is defined to be the set of vectors in $\mathbb{F}^n_2$ whose dot product with the set of vector $\bm{v}_1, \bm{v}_2, \ldots, \bm{v}_m \in \mathbb{F}^n_2$ is zero. 

:::{dropdown} Dot Product as a Parity Check

Consider a $3$ bit string encoded as $4$ physical bits, 
\begin{equation}
\bm{a} = \begin{bmatrix}
a_1 \\
a_2 \\
a_3 \\
a_1 \oplus a_3
\end{bmatrix}, 
\end{equation}
where the $4$th physical bit stores the parity check bit $a_1 \oplus a_3$. 

If this is valid code word, and one wants to check to see if it remains a valid codeword, this can be done through the vector 
\begin{equation}
\bm{v} = \begin{bmatrix}
1 \\
0 \\
1 \\
1
\end{bmatrix},
\end{equation}
as 
\begin{equation}
\bm{a} \cdot \bm{v} = \begin{bmatrix}
a_1 \\
a_2 \\
a_3 \\
a_1 \oplus a_3
\end{bmatrix} \cdot \begin{bmatrix}
1 \\
0 \\
1 \\
1
\end{bmatrix} = a_1 \oplus a_3 \oplus (a_1 \oplus a_3).
\end{equation}
Hence, if there has been a bit-flip on either the $1$st, $3$rd or $4$th bit (the parity bit), then $\bm{a} \cdot \bm{v} \neq 0$. 

:::

As above, consider a code encoding $k$ logical bits into $n$ physical bits, such that $p=n-k$ parity bits are used for the error correction. Then, the parity checks can be formulated in terms of a parity matrix $H$ as
\begin{equation}
H = \left[
\begin{array}{c}
  A_{p \times k} ~ \vert ~ \mathbb{I}_{p \times p} \\
\end{array}
\right],
\end{equation}
such that $\mathbb{I}_{p \times p}$ is the $k \times k$ identity matrix and $A_{p \times k}$ is an $p \times k$ matrix that encodes which parity checks occur. Note, $A_{p \times k}$ is the same as in the [generating matrix](#generating_matrix_target).

If $\bm{y} \in \mathbb{F}^n_2$ is an encoded bit-string, then its a code word if and only if
\begin{equation}
H \bm{y} = 0.
\end{equation} 
The codespace can therefore be defined more formally as the [kernel](#kernal_linear_maps_target) of the parity check matrix. 

***Examples***

:::{dropdown} [Error Detection With Parity](#error_detection_with_parity_example)

The parity matrix of this code is 
\begin{equation}
H = \left[
\begin{array}{cccc}
  1 & 1 & 1 ~\vert ~ 1
\end{array}
\right].
\end{equation}

Now, consider an arbitrary code work 
\begin{equation}
\bm{a} = \begin{bmatrix}
a_1 \\
a_2 \\
a_3 \\
a_1 \oplus a_2 \oplus a_3 
\end{bmatrix}.
\end{equation}

It can then be seen that 
\begin{align*}
H \bm{a} &= \left[
\begin{array}{cccc}
  1 & 1 & 1 ~\vert ~ 1
\end{array}
\right] \begin{bmatrix}
a_1 \\
a_2 \\
a_3 \\
a_1 \oplus a_2 \oplus a_3 
\end{bmatrix} \\
&= a_1 \oplus a_2 \oplus a_3 \oplus (a_1 \oplus a_2 \oplus a_3) \\
&= 0.
\end{align*}
:::

:::{dropdown} [Error Correction With Parity](#error_correction_with_parity_example)

The parity matrix of this code is 
\begin{equation}
H = \left[
\begin{array}{cccccc}
 1 & 1 & 0 ~ \vert ~ 1 & 0 & 0 \\
 1 & 0 & 1 ~ \vert ~ 0 & 1 & 0 \\
 0 & 1 & 1 ~ \vert ~ 0 & 0 & 1
\end{array}
\right].
\end{equation}

Now, consider an arbitrary code work 
\begin{equation}
\bm{a} = \begin{bmatrix}
a_1 \\
a_2 \\
a_3 \\
a_1 \oplus a_2  \\
a_1 \oplus a_3  \\
a_2 \oplus a_3  \\
\end{bmatrix}.
\end{equation}

It can then be seen that 
\begin{align*}
H \bm{a} &= \begin{bmatrix}
a_1 \oplus a_2 \oplus (a_1 \oplus a_2) \\
a_1 \oplus a_3 \oplus (a_1 \oplus a_3) \\
a_2 \oplus a_3 \oplus (a_2 \oplus a_3) \\
\end{bmatrix} \\
&= \bm{0}.
\end{align*}

:::

#### Error Syndromes

Given an unknown encoded bit-string $\bm{y}' \in \mathbb{F}^n_2$, the syndrome of the code $\bm{s} \in \mathbb{F}^p_2$ is given by 
\begin{equation}
\bm{s} = H \bm{y}'.
\end{equation}
The aim is then for the syndrome $\bm{s} \in \mathbb{F}^p_2$ to determine where an error occurred. 

***Examples***


:::{dropdown} [Error Correction With Parity](#error_correction_with_parity_example)

The parity matrix of this code is 
\begin{equation}
H = \left[
\begin{array}{cccccc}
 1 & 1 & 0 ~ \vert ~ 1 & 0 & 0 \\
 1 & 0 & 1 ~ \vert ~ 0 & 1 & 0 \\
 0 & 1 & 1 ~ \vert ~ 0 & 0 & 1
\end{array}
\right].
\end{equation}

Now, consider an arbitrary code word $\bm{y}$ where an error occurs on the $2$ logical bit
\begin{equation}
\bm{y} = \begin{bmatrix}
y_1 \\
y_2 \\
y_3 \\
y_1 \oplus y_2  \\
y_1 \oplus y_3  \\
y_2 \oplus y_3  \\
\end{bmatrix}
\rightarrow \bm{y}' = \begin{bmatrix}
y_1 \\
y_2 \oplus 1 \\
y_3 \\
y_1 \oplus y_2  \\
y_1 \oplus y_3  \\
y_2 \oplus y_3  \\
\end{bmatrix}.
\end{equation}
It can then be seen that the syndrome will be 
\begin{align*}
H \bm{y}' &= \begin{bmatrix}
y_1 \oplus (y_2 \oplus 1) \oplus (y_1 \oplus y_2) \\
y_1 \oplus y_3 \oplus (y_1 \oplus y_3) \\
(y_2 \oplus 1) \oplus y_3 \oplus (y_2 \oplus y_3) \\
\end{bmatrix} \\
&= \begin{bmatrix}
1 \\ 
0 \\ 
1
\end{bmatrix},
\end{align*}
as expected from the error syndromes of the code detailed [here](#error_syndromes_of_parity_error_correction).


:::

