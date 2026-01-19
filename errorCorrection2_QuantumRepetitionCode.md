---
title: Quantum Repetition Codes
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
keywords: qubits, Repetition Code, bit-flips, phase errors.  
abstract: The bit-flip and phase-flip quantum repetition codes.  
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(error_correction_repetition_code_page_target)=
The Quantum Repetition Code comes in two flavours, one protects against bit-flip errors and the other protects against phase-flip errors. As with the classical repetition code, the code works by increasing the size of the Hilbert space, allowing logical qubits to be encoded in multiple physical qubits.  


(target_error_correction_2_bit_repetition_code)=
## The 2-Qubit Bit-flip Repetition Code

This code encodes one logical qubit in two physical qubits and is able to detect a single bit-flip $\big(X \big)$ error.

The code-words of the code are
\begin{equation}
\ket{0}_{L} \rightarrow \ket{00}, ~~~ \ket{1}_L \rightarrow \ket{11}, 
\end{equation}
such that an arbitrary qubit can be encoded as
\begin{align*}
\ket{\psi} = \alpha \ket{0} + \beta \ket{1} \xrightarrow{\rm encoder} \ket{\psi}_L = \alpha \ket{00} + \beta \ket{11}
\end{align*}
The part of the expanded Hilbert space in which the logical information is encoded is called the code space, given here by 
\begin{equation}
\mathfrak{C}_2 = {\rm Span} \{ \ket{00}, \ket{11} \}.
\end{equation}
The aim of the code is to detect if an error on the physical qubits have caused the state to leave the code space without disturbing the encoded information. 

Consider measuring the following operator on the state,
(z1_z2_operator_form)=
\begin{align*}
Z_1 \otimes Z_2 &= \big( \ket{0}\bra{0} - \ket{1}\bra{1} \big) \otimes \big( \ket{0}\bra{0} - \ket{1}\bra{1} \big), \\
&= \ket{00}\bra{00} - \ket{01}\bra{01} - \ket{10}\bra{10} + \ket{11}\bra{11}, \\
&= \ket{\Phi_{00}^{+}}\bra{\Phi_{00}^{+}} + \ket{\Phi_{01}^{+}}\bra{\Phi_{01}^{+}} - \ket{\Phi_{10}^{+}}\bra{\Phi_{10}^{+}} - \ket{\Phi_{11}^{+}}\bra{\Phi_{11}^{+}},
\end{align*}
where in the final line $Z_1 \otimes Z_2$ has been written in its eigenbasis, namely the [Bell basis](#bell_states_teleportation_target) [💭](parity_check_operator_target_glossary). 

Firstly, it can be seen that measuring $Z_1 \otimes Z_2$ on any state supported only within $\mathfrak{C}_2$ always gives a measurement outcome of $(+1)$ **and** returns the state unchanged, 
\begin{equation}
\big(Z_1 \otimes Z_2 \big)\big( \alpha \ket{00} + \beta \ket{11} \big) = \alpha \ket{00} + \beta \ket{11}.
\end{equation}
Consider now that an $X$-error occurs on the first qubit, 
\begin{equation}
X_1 \ket{\psi}_L = \alpha \ket{10} + \beta \ket{01},
\end{equation}
where the notation $X_1 = X_1 \otimes \mathbb{I}_2$ has been used. A measurement of $Z_1 \otimes Z_2$ on this state would give an outcome of $(-1)$. Likewise, if an $X$-error occurs on the second qubit, 
\begin{equation}
X_2 \ket{\psi}_L = \alpha \ket{01} + \beta \ket{10},
\end{equation} 
a measurement of $Z_1 \otimes Z_2$ would also give an outcome of $(-1)$. If, instead, an $X$-error occurs on both qubits,
\begin{equation}
X_1X_2 \ket{\psi}_L =  \alpha \ket{11} + \beta \ket{00},
\end{equation} 
then a measurement of $Z_1 \otimes Z_2$ would give an outcome of $(+1)$.

The outcome of measuring $Z_1 \otimes Z_2$ can therefore be used as a syndrome. If a single $X$ error occurs, then a measurement of $Z_1 \otimes Z_2$ is enough to detect that an error has occurred. Although, it is not enough to know if that error occurred on the first or the second qubit as both of these errors lead to the same measurement outcome. Therefore, the error cannot be corrected, only detected, as its location is not known. If, on the other hand, an $X$-error has occurred on both qubits, a measurement of $Z_1 \otimes Z_2$ is not enough to determine if an error has occurred. This is a result of the qubit remaining in $\mathfrak{C}_2$ under an $X_1X_2$ error and therefore leading to a measurement result of $(+1)$. This situation is therefore indistinguishable from no error having occurred.  

In addition to not being able to detect a $X_1X_2$ error, the 2-qubit bit-flip repetition code is also unable to protect against phase errors $\big(Z$-errors$\big)$. For example, consider the error 
\begin{equation}
Z_1 \ket{\psi}_L = \alpha \ket{00} - \beta \ket{11}.
\end{equation}
A measurement of $Z_1 \otimes Z_2$ would give an outcome of $(+1)$ as this state remains in $\mathfrak{C}_2$. Hence, a $Z_1$ error is also indistinguishable from no error having occurred and hence cannot be detected using $Z_1 \otimes Z_2$. The same if true of a $Z_2$ error. 

The 2-qubit bit-flip repetition code is therefore only useful for detecting errors in the set $\{\mathbb{I}, X_1, X_2 \}$. In summary, and using the notation ${\rm error} \rightarrow {\rm syndrome}$ (with the eigenvalue $+1$ mapped to $0$ and the eigenvalue $-1$ mapped to $1$), the errors and corresponding syndromes of the code are 
\begin{align*}
\mathbb{I} &\rightarrow 0, \\
X_1 &\rightarrow 1, \\
X_2 &\rightarrow 1. 
\end{align*}


### Code Distance

To find the [code distance](#Code_distance_target_glossary) of the 2-qubit bit-flip repetition code, one must find the minimum number of physical qubits upon which an error must act in order to change one logical code word to another. When considering $X$-errors above, this looks to be 2 as 
\begin{equation}
X_1X_2 \ket{00} = \ket{11}, ~ ~ ~ X_1X_2 \ket{11} = \ket{00}.
\end{equation}
However, quantum systems are also susceptible to $Z$-errors. To see the effect of these, consider now the logical basis of the $X$ operator, 
\begin{equation}
\ket{+}_L = \frac{1}{\sqrt{2}} \big( \ket{00} + \ket{11} \big), ~ ~ ~ \ket{-}_L = \frac{1}{\sqrt{2}} \big( \ket{00} - \ket{11} \big), 
\end{equation}
Any logical qubit can be written in this basis, with $\ket{+}_L$ and $\ket{-}_L$ now being the code words. However, a single $Z$-error can move one between these code words
\begin{equation}
Z_i \ket{+}_L = \ket{-}_L, ~ ~ ~ Z_i \ket{-}_L = \ket{+}_L ~ ~ ~ \forall ~ ~ i ~ \in ~ \{1,2\}.
\end{equation}
Hence, the code distance is 1, not 2. 

Alternatively, the distance of a code is the minimum number of errors that will go undetected. Therefore, from above, one can see that the code distance is 1 as a single $Z$ error went undetected due to it not mapping the state outside of $\mathfrak{C}_2$. 

## The 3-Qubit Bit-flip Repetition Code

The 3-qubit bit-flip repetition code functions very similarly to the 2-qubit version, however, with one logical qubit instead encoded into three physical qubits. As a result, the 3-qubit bit-flip repetition code is able to **correct** one bit-flip error and detect up to two bit-flip errors.

The code-words of the code are
\begin{equation}
\ket{0}_{L} \rightarrow \ket{000}, ~~~ \ket{1}_L \rightarrow \ket{111}, 
\end{equation}
such that an arbitrary qubit can be encoded as
\begin{align*}
\ket{\psi} = \alpha \ket{0} + \beta \ket{1} \xrightarrow{\rm encoder} \ket{\psi}_L = \alpha \ket{000} + \beta \ket{111},
\end{align*}
with code space then 
\begin{equation}
\mathfrak{C}_3 = {\rm Span} \{ \ket{000}, \ket{111} \}.
\end{equation}

The following operators are then measured,
\begin{align*}
Z_1 \otimes Z_2 \otimes \mathbb{I}_3, \\
\mathbb{I}_1 \otimes Z_2 \otimes Z_3,
\end{align*}
where the operators on the $1,2$ and $2,3$ qubits respectively are as [above](#z1_z2_operator_form) in the 2-qubit bit-flip repetition code. 

Once again, a measurement of either $Z_1 \otimes Z_2 \otimes \mathbb{I}_3$ or $\mathbb{I}_1 \otimes Z_2 \otimes Z_3$ on any state supported only within $\mathfrak{C}_3$ always gives a measurement outcome of $(+1)$ **and** returns the state unchanged, 
\begin{align*}
Z_1 \otimes Z_2 \otimes \mathbb{I} \big( \alpha \ket{000} + \beta \ket{111} \big) =  \big( \alpha \ket{000} + \beta \ket{111} \big).
\end{align*}

We label the measurement outcome of $Z_1 \otimes Z_2 \otimes \mathbb{I}_3$ as $\lambda_1$ and $\mathbb{I}_1 \otimes Z_2 \otimes Z_3$ as $\lambda_2$, such that the syndrome is $(\lambda_1, \lambda_2)$. The following error/syndrome relationship can then be shown
\begin{align*}
\mathbb{I} &\rightarrow (0,0), \\
X_3 &\rightarrow (0,1), \\
X_2 &\rightarrow (1,1), \\
X_1 &\rightarrow (1,0). 
\end{align*}

Therefore, if only a single qubit bit-flip occurs, a measurement of these operators is enough to not only detected that an error has occurred, but also uniquely identify where it occurred such that it can be corrected. To correct the error, one just applies $X$ on the qubit in which they identified the error occurred.   

If one also considers the possibility of 2 qubit $X$-errors also occurring then the syndromes become non-unique, 
\begin{align*}
X_2X_3 &\rightarrow (1,0), \\
X_1X_3 &\rightarrow (1,1), \\
X_1X_2 &\rightarrow (0,1). 
\end{align*}

If a three qubit $X$-error occurs, the state remains in $\mathfrak{C}$, giving 
\begin{align*}
X_1X_2X_3 &\rightarrow (0,0),
\end{align*}
which is indistinguishable from no error having occurred.

The 3-qubit bit-flip repetition code is therefore able to **correct** errors in the set $\{\mathbb{I}, X_1, X_2, X_3\}$, it is able to **detect** errors in the set 
\begin{equation}
\{\mathbb{I}, X_1, X_2, X_3, X_1X_2, X_1X_3, X_2X_3 \}.
\end{equation}