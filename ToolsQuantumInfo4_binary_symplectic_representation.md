---
title: Binary Symplectic Representation
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
keywords: Pauli Strings, Complete Basis, Binary.   
abstract: Details, properties and applications of the Pauli Group   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

Elements of the Pauli-strings can be mapped to the $2n$ bit-strings via the binary symplectic representation. 

## Single Qubit

The $1$-qubit Pauli-strings are
\begin{equation}
\mathcal{P} = \big\{\mathbb{I}, X, Z, Y \big\}.
\end{equation}

Any element of $P_j \in \mathcal{P}$ can be written as 
\begin{equation}\label{eq: single qubit Pauli}
P_j = (-i)^{z_j \cdot x_j} Z^{z_j} X^{x_j},
\end{equation}
where $z_j,x_j \in \{0,1\}^1$, meaning that $P_j$ can be captured by the $2$-bit string 
\begin{equation}
p_j = (x_j \mid z_j) \in \{0,1\}^{2}.
\end{equation}
The $(-i)^{z_j \cdot x_j}$ phase term ensures the correct behavior when multiply the Pauli-strings.

:::{dropdown} **Single Qubit Mappings**
\begin{align*}
\mathbb{I} = (-i)^{0 \cdot 0} Z^0 X^0 \longrightarrow (0 \mid 0) \\
{X} = (-i)^{0 \cdot 1} Z^0 X^1 \longrightarrow (1 \mid 0) \\
{Z} = (-i)^{1 \cdot 0} Z^1 X^0 \longrightarrow (0 \mid 1) \\
{Y} = (-i)^{1 \cdot 1} Z^1 X^1 \longrightarrow (1 \mid 1) \\
\end{align*}

As $ZX = -iY$, it can be seen that the phase term ensures the correct multiplication behavior. 

:::

### Multiplication of Single Qubit Pauli's

Consider two elements of the single qubit Pauli-string and their mappings to $2$-bit-strings
\begin{equation}
P_j \rightarrow p_j = (x_j \mid z_j) ~ ~ {\rm and} ~ ~ P_k \rightarrow p_k = (x_k \mid z_k).
\end{equation}
Then 
\begin{equation}
P_jP_k = (-1)^{z_j \cdot x_k} P_l : P_l \rightarrow p_l = (x_j \oplus x_k \mid z_j \oplus z_k),
\end{equation}
Similarly, 
\begin{equation}
P_kP_j = (-1)^{z_k \cdot x_j} P_l : P_l \rightarrow p_l = (x_j \oplus x_k \mid z_j \oplus z_k).
\end{equation}
:::{dropdown} **Proof**
\begin{align*}
P_jP_k &= \big[ (-1)^{z_j \cdot x_j} Z^{z_j} X^{x_j} \big] \big[ (-1)^{z_k \cdot x_k} Z^{z_k} X^{x_k} \big] \\
&= (-1)^{z_j \cdot x_j \oplus z_k \cdot x_k} Z^{z_j} X^{x_j} Z^{z_k} X^{x_k} \\
&= (-1)^{z_j \cdot x_j \oplus z_k \cdot x_k} (-1)^{z_k \cdot x_j} Z^{z_j \oplus z_k} X^{x_j \oplus x_k} \\
&= (-1)^{(z_j \cdot x_j) \oplus (z_k \cdot x_k) \oplus (z_k \cdot x_j)} Z^{z_j \oplus z_k} X^{x_j \oplus x_k} \\
&= (-1)^{(z_j \cdot x_j) \oplus (z_k \cdot x_k) \oplus (z_k \cdot x_j) \oplus (z_j \cdot x_k)}(-1)^{z_j \cdot x_k} Z^{z_j \oplus z_k} X^{x_j \oplus x_k} \\
&= (-1)^{z_j \cdot x_k} [ (-1)^{(z_j \oplus z_k) \cdot (x_j \oplus x_k)}Z^{(z_j \oplus z_k)} X^{(x_j \oplus x_k)} ] \\
&= (-1)^{z_j \cdot x_k} P_l,
\end{align*}
such that 
\begin{equation}
P_l = (-1)^{z_l \cdot x_l}Z^{z_l} X^{x_l},
\end{equation}
with $z_l = z_j \oplus z_k$ and $x_l = x_j \oplus x_k$. 

Note, in the above we have used the fact that 
\begin{equation}
X^{x_j} Z^{z_k} = (-1)^{x_j \cdot z_k} Z^{z_k} X^{x_j}.
\end{equation}

It can then be seen that 
\begin{align*}
P_kP_j &= \big[ (-1)^{z_k \cdot x_k} Z^{z_k} X^{x_k} \big] \big[ (-1)^{z_j \cdot x_j} Z^{z_j} X^{x_j} \big]  \\
&= (-1)^{z_k \cdot x_j} [ (-1)^{(z_j \oplus z_k) \cdot (x_j \oplus x_k)}Z^{(z_j \oplus z_k)} X^{(x_j \oplus x_k)} ] \\
&= (-1)^{z_k \cdot x_j} P_l.
\end{align*}
:::

### Commutation of Single Qubit Pauli's

From the above it can be seen that 
\begin{equation}
P_jP_k = (-1)^{(z_k \cdot x_j) \oplus (z_j \cdot x_k)} P_kP_j.
\end{equation}
Therefore, the Pauli-strings represented by the bit-strings 
\begin{equation}
p_j = (x_j \mid z_j) ~ ~ {\rm and} ~ ~ p_k = (x_k \mid z_k)
\end{equation}
commute if
\begin{equation}
(z_j \cdot x_k) \oplus (z_k \cdot x_j) = 0 ~ {\rm mod}~2,
\end{equation}
which is the binary symplectic inner product of these bit-strings.

## $n$-qubits Pauli-strings

The $n$-qubit Pauli-strings are the $n$ fold tensor product of the single qubit Pauli's:
\begin{equation}
P = \bigotimes_{j=1}^n P_j : P_j \in \big\{\mathbb{I}, X, Z, Y \big\}~\forall~j.
\end{equation}
Using the definition for single qubit Pauli's given above, this becomes 
\begin{align*}
P &= \bigotimes_{j=1}^n (-i)^{z_j \cdot x_j} Z^{z_j} X^{x_j} \\
&= (-i)^{\bm{z} \cdot \bm{x}} \bigotimes_{j=1}^n Z^{z_j} X^{x_j},
\end{align*}
where $\bm{x} = (x_1x_2 \ldots x_n)$ and $\bm{z} = (z_1z_2 \ldots z_n)$, such that $\bm{x}, \bm{z} \in \{0,1\}^n$.

Hence, an $n$-qubit Pauli string can be represented by the $2n$ bit-string 
\begin{equation}
P \rightarrow p = (\bm{x} \mid \bm{z}).
\end{equation}

### Multiplication of Multi-Qubit Pauli's

Consider two elements of the single qubit Pauli-string and their mappings to $2$-bit-strings
\begin{equation}
P \rightarrow p = (\bm{x}_p \mid \bm{z}_p) ~ ~ {\rm and} ~ ~ Q \rightarrow q = ({\bm{x_q}} \mid \bm{z}_q).
\end{equation}
Then 
\begin{equation}
PQ = (-1)^{\bm{z}_p \cdot \bm{x}_q} L : L \rightarrow l = (\bm{x}_p \oplus \bm{x}_q \mid \bm{z}_p \oplus \bm{z}_q),
\end{equation}
Similarly, 
\begin{equation}
QP = (-1)^{\bm{z}_q \cdot \bm{x}_p} L : L \rightarrow l = (\bm{x}_p \oplus \bm{x}_q \mid \bm{z}_p \oplus \bm{z}_q).
\end{equation}

:::{dropdown} **Proof**

\begin{align*}
PQ &= \biggl[ (-i)^{\bm{z}_p \cdot \bm{x}_p} \bigotimes_{j=1}^n Z^{z^p_j} X^{x^p_j} \biggl] \biggl[ (-i)^{\bm{z}_q \cdot \bm{x}_q} \bigotimes_{j=1}^n Z^{z^q_j} X^{x^q_j} \biggl] \\
&= (-i)^{(\bm{z}_p \cdot \bm{x}_p) \oplus (\bm{z}_q \cdot \bm{x}_q)} \bigg[  \bigotimes_{j=1}^n Z^{z^p_j} X^{x^p_j} Z^{z^q_j} X^{x^q_j} \bigg] \\
&= (-i)^{(\bm{z}_p \cdot \bm{x}_p) \oplus (\bm{z}_q \cdot \bm{x}_q)} \bigg[  \bigotimes_{j=1}^n (-i)^{(z^q_j \cdot x^p_j)} Z^{z^p_j \oplus z^q_j} X^{x^p_j \oplus x^q_j} \bigg] \\
&= (-i)^{(\bm{z}_p \cdot \bm{x}_p) \oplus (\bm{z}_q \cdot \bm{x}_q)} (-i)^{\bm{z}_q \cdot \bm{x}_p} \bigg[  \bigotimes_{j=1}^n Z^{z^p_j \oplus z^q_j} X^{x^p_j \oplus x^q_j} \bigg] \\
&= (-i)^{(\bm{z}_p \cdot \bm{x}_p) \oplus (\bm{z}_q \cdot \bm{x}_q) \oplus (\bm{z}_q \cdot \bm{x}_p) \oplus (\bm{z}_p \cdot \bm{x}_q)} (-1)^{(\bm{z}_p \cdot \bm{x}_q)}  \bigg[  \bigotimes_{j=1}^n Z^{z^p_j \oplus z^q_j} X^{x^p_j \oplus x^q_j} \bigg] \\
&= (-1)^{(\bm{z}_p \cdot \bm{x}_q)} \bigg[ (-i)^{(\bm{z}_p \oplus \bm{z}_q) \cdot (\bm{x}_p \oplus \bm{x}_q)}  \bigotimes_{j=1}^n Z^{z^p_j \oplus z^q_j} X^{x^p_j \oplus x^q_j} \bigg] \\
&=  (-1)^{(\bm{z}_p \cdot \bm{x}_q)} L,
\end{align*}
such that 
\begin{equation}
L = (-1)^{\bm{z}_l \cdot \bm{x}_l}Z^{\bm{z}_l} X^{\bm{x}_l},
\end{equation}
with $\bm{z}_l = \bm{z}_j \oplus \bm{z}_k$ and $\bm{x}_l = \bm{x}_j \oplus \bm{x}_k$. 

Note, in the above we have used the fact that 
\begin{equation}
X^{x_j} Z^{z_k} = (-1)^{x_j \cdot z_k} Z^{z_k} X^{x_j}.
\end{equation}

It can then be seen that 
\begin{align*}
QP &= \biggl[ (-i)^{\bm{z}_q \cdot \bm{x}_q} \bigotimes_{j=1}^n Z^{z^q_j} X^{x^q_j} \biggl] \biggl[ (-i)^{\bm{z}_p \cdot \bm{x}_p} \bigotimes_{j=1}^n Z^{z^p_j} X^{x^p_j} \biggl] \\
&= (-1)^{(\bm{z}_q \cdot \bm{x}_p)} \bigg[ (-i)^{(\bm{z}_p \oplus \bm{z}_q) \cdot (\bm{x}_p \oplus \bm{x}_q)}  \bigotimes_{j=1}^n Z^{z^p_j \oplus z^q_j} X^{x^p_j \oplus x^q_j} \bigg] \\
&=  (-1)^{(\bm{z}_q \cdot \bm{x}_p)} L.
\end{align*}
:::

### Commutation of Multi-Qubit Pauli's

From the above, it can be seen that 
\begin{equation}
PQ = (-1)^{(\bm{z}_p \cdot \bm{x}_q) \oplus (\bm{z}_q \cdot \bm{x}_p)} QP.
\end{equation}
Therefore, the Pauli-strings represented by the bit-strings 
\begin{equation}
p = (\bm{x}_p \mid \bm{z}_p) ~ ~ {\rm and} ~ ~ q = (\bm{x}_q \mid \bm{z}_q)
\end{equation}
commute if
\begin{equation}
(\bm{z}_p \cdot \bm{x}_q) \oplus (\bm{z}_q \cdot \bm{x}_p) = 0 ~ {\rm mod}~2,
\end{equation}
which is the binary symplectic inner product of these bit-strings. 