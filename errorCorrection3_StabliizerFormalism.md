---
title: Stabilizer Formalism 
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
abstract: The stabilizer formalism of quantum error correction.   
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

The stabilizer formalism is a method for creating error correcting codes using the Pauli-group. In addition to allowing certain errors to be detected and corrected, logical gates can also be performed in this framework. 

## Pauli-group 

The generators of the qubit Pauli-group are
\begin{equation}
\mathcal{P}_1 = \langle X, Z, i\mathbb{I} \rangle.
\end{equation}
From these operators all elements of the one qubit Pauli-group can be generated. The Pauli-group is the set of Pauli-operators plus identity with all possible phases of $\{\pm 1, \pm i \}$. 

The $n$-qubit Pauli-group , $\mathcal{P}_n$, is then the $n$-fold tensor product of elements in the one qubit Pauli-group. All elements in $\mathcal{P}_n$ either commute or anit-commute,
\begin{equation}
P_1P_2 = (\pm)P_2P_1 ~~ \forall ~ ~ P_1, P_2~\in~\mathcal{P}_n,
\end{equation} 

All elements of the Pauli-group have eigenvalues $\{+1, -1\}$ or $\{+i, -i\}$. Here, we mostly consider just the elements with eigenvalues $\{+1, -1\}$ (the Hermitian elements of the Pauli-group). 

See the [Pauli Group Page](#Pauli_group_page_target) for more detail.

## Stabilizer Codes

### Definition

The stabilizers of an error correcting code are defined as 
\begin{equation}
\mathcal{S} = \big\{ P_i \in \mathcal{P}_n: P_i \ket{\psi}_L = \ket{\psi}_L~\forall~\ket{\psi}_L \wedge [P_i, P_j] = 0 ~ \forall ~ (i,j) \big\},
\end{equation}
such that $-\mathbb{I} \notin \mathcal{S}$. The stabilizers are therefore an [Abelian subgroup](#Abelian_group_target_glossary) of the $n$-qubit Pauli-group, $\mathcal{P}_n$, such that all logical states (states in the code space) are $(+1)$ eigenstates of each stabilizer, that does not contain the negative identity operator. 

The justification of these conditions are as follows:

1. $P_i \ket{\psi}_L = \ket{\psi}_L~\forall~\ket{\psi}_L$:
    
    This avoids any logical information encoded in the code space being destroyed when a stablizer is measured on $\ket{\psi}_L$.

    :::{dropdown} Further Details

    A state, $\ket{\omega}$ is said to be stabilized by an operator $U$ if $U\ket{\omega} = \ket{\omega}$, meaning $\ket{\omega}$ is a $(+1)$ eigenstate of $U$. 
    
    From the above definition of $\mathcal{S}$, it can be seen that $\forall~P_i \in \mathcal{S}$ all logical states $\ket{\psi}_L$ are stabilized by $P_i$. Therefore, if one were to measure or apply $P_i$ on any logical state $\ket{\psi}_L$ they would return the state $\ket{\psi}_L$ unchanged. This avoids any logical information encoded in the code space being destroyed when a stablizer is measured on $\ket{\psi}_L$. (Does it also prevent loss of logical information in general? I am currently not sure). 
    
    One can reverse this definition, and defined the code space to be the subspace of the total Hilbert space that is stabilized by all elements of $\mathcal{S}$. Phrased alternatively, the code space is defined as the intersection of all $(+1)$ eigenspaces of the elements of $\mathcal{S}$.  
    :::

2. $[P_i, P_j] = 0$:

    If this condition is not met, only the trivial space can be stabilized. 

    :::{dropdown} Proof
 
    Let $P_i, P_j \in \mathcal{P}_n$ such that $[P_i, P_j] \neq 0$. Moreover, assume they both stabilize $\ket{\psi}_L$ such that 
    \begin{equation}
    P_i \ket{\psi}_L = P_j \ket{\psi}_L = \ket{\psi}_L.
    \end{equation}

    Firstly, note that given that all elements of $\mathcal{P}_n$ commute or anti-commute,
    \begin{equation}
    [P_i, P_j] \neq 0  \implies P_iP_j + P_jP_i = 0.
    \end{equation}
    Secondly, the products, $P_iP_j$ and $P_jP_i$ also stabilize $\ket{\psi}_L$ if $P_i$ and $P_j$ individually stabilize $\ket{\psi}_L$, such that 
    \begin{align*}
    P_iP_j \ket{\psi}_L &= \ket{\psi}_L, \\
    P_jP_i \ket{\psi}_L &= \ket{\psi}_L.
    \end{align*}

    Putting these facts together implies that 
    \begin{align*}
    P_jP_i \ket{\psi}_L &= - P_iP_j \ket{\psi}_L, \\
    &=  - \ket{\psi}_L, \\
    &= \ket{\psi}_L. 
    \end{align*}
    This is only true if $\ket{\psi}_L = 0$, meaning that non-[Abelian subgroups](#Abelian_group_target_glossary) of $\mathcal{P}_n$ can only stabilize a trivial subspace. 

    (Note, the equation $\ket{\psi}=-\ket{\psi}$ is about the physical equivalence of vectors in a Hilbert space, with this equation only being satasfied for the zero vector. It is not about whether two states are physically distinguishable under global phases.)

    :::

3. $- \mathbb{I} \notin \mathcal{S}$: 

    If this condition is not met, only the trivial space can be stabilized.  

    :::{dropdown} Proof
 
    All states are stabilized by $\mathbb{I}$, 
    \begin{equation}
      (\mathbb{I} ) \ket{\psi}_L = \ket{\psi}_L.
    \end{equation}
    Hence, $\mathbb{I} \in \mathcal{S}$ for all possible $\mathcal{S}$. 
    
    If one assumes that $-\mathbb{I} \in \mathcal{S}$, then one needs 
    \begin{equation}
    \big( - \mathbb{I} \big) \ket{\psi}_L = \ket{\psi}_L,
    \end{equation}
    by definition of $\mathcal{S}$. Combining these two facts implys that 
    \begin{equation}
    \ket{\psi}_L = - \ket{\psi}_L, 
    \end{equation}
    which is only true if $\ket{\psi}_L = 0$, meaning that $\mathcal{S}$ would only stabilize a trivial subspace. 

    :::

### The Role of the Stabilizers

The stabilizers are used to separate a Hilbert space into a series of orthogonal subspaces, as per the structure of [QEC codes](#QEC_Structure_page). 

Each stabliser, $P_i$, is an element of the Pauli-group and can therefore be written as
\begin{equation}
P_i = \Pi^i_{+1} - \Pi^i_{-1},
\end{equation}
where $\Pi^i_{+1}$ is the projector onto the $+1$ eigenspace of $P_i$ and $\Pi^i_{-1}$ the projector onto the $-1$ eigenspace of $P_i$. One can then defined the code space via the projector
\begin{equation}
\Pi_{\mathfrak{C}_L} = \cap_{i=0}^{\vert \mathcal{S} \vert} \Pi^i_{+1},
\end{equation}
which is the projector onto the intersection of all the positive eigenspaces of the stabilizers. 

The intersection of all the different combinations of the positive and negative eigenspaces of the stabilizers are all pairwise orthogonal, and they define each of the orthogonal subspaces of the QEC code.  

An error that maps the code space to one of these orthogonal subspaces can therefore be detected by measuring the observable who's eigenspaces are exactly these orthogonal subspaces.  

<!-- Given the set of stabilizers is defined for an arbitrary state within the code space, the set of stablizers should be thought of as stabilizing the code space rather than a given logical state. In reality, the code space is defined in the opposite direction: e -->

### Measuring Stabilizer 

All elements of $\mathcal{P}_n$ are [unitary](#target_unitary_adjoint_page_unitary_definition). If $P \in \mathcal{P}_n$ is also [Hermitian](#hermitian_adjoint_page_target), then any stabilizer $P$ can be measured on the logic state indirectly, with the measurement outcome stored in an ancilla [💭](#anti_hermitain_pauli_stab_measures_target_glossary).

```{figure} errorCorrectionStabMeasureCircuit.png
:alt: 
:class: bg-primary
:width: 600px
:align: center
:target: stab_measure_circuit_target

A schematic of the circuit used to measure the stabilizer $P$ on the logical state $\ket{\psi}_L$. 
```

Assume that $P \in \mathcal{P}_n$ is a stabilizer of the logical state $\ket{\psi}_L$ such that $P \ket{\psi}_L = \ket{\psi}_L$. Let $E$ be some correctable error that has occurred on the logical state, such that $P ( E \ket{\psi}_L) = E \ket{\psi}_L$ or $P ( E \ket{\psi}_L) = - E \ket{\psi}_L$, depending on whether $E \ket{\psi}_L$ is in the positive or negative eigenspace of $P$. 

The input state into the circuit is $E\ket{\psi}_L \ket{0}_A$, where $A$ labels the ancillary space and the $L$ subscript now doubles as a label for the space of the logical state.  

The output state is then 
\begin{equation}
\frac{1}{2} \big( \mathbb{I}_L \otimes \mathbb{I}_A + P_L \otimes \mathbb{I}_A) E \ket{\psi}_L \ket{0}_A + \frac{1}{2} \big( \mathbb{I}_L \otimes \mathbb{I}_A - P_L \otimes \mathbb{I}_A) E \ket{\psi}_L \ket{1}_A.
\end{equation}

:::{dropdown} Proof

The input state to the circuit is 
\begin{equation}
E\ket{\psi}_L \otimes \ket{0}_A.
\end{equation}
The controlled stabilizer gate can be written as 
\begin{equation}
P_LC_A = \mathbb{I}_L \otimes \ket{0}\bra{0}_A + P_L \otimes \ket{1}\bra{1}_A.
\end{equation}
The output state of the circuit is then 
\begin{align*}

&(\mathbb{I} \otimes H) P_L C_A (\mathbb{I} \otimes H) \big(E\ket{\psi}_L \otimes \ket{0}_A \big) \\
=& (\mathbb{I} \otimes H)\big(\mathbb{I}_L \otimes \ket{0}\bra{0}_A + P_L \otimes \ket{1}\bra{1}_A \big)\big(E \ket{\psi}_L \otimes \ket{+} \big) \\
=& \frac{1}{\sqrt{2}}(\mathbb{I} \otimes H) \big( E\ket{\psi}_L \otimes \ket{0} + PE\ket{\psi}_L \otimes \ket{1}   \big) \\
=& \frac{1}{\sqrt{2}}\big( E\ket{\psi}_L \otimes \ket{+} + PE\ket{\psi}_L \otimes \ket{-}   \big).\\
\end{align*}
Expanding $\ket{+}$ and $\ket{-}$ in the computational basis and factorising completes the proof. 
:::

Therefore, if $P ( E \ket{\psi}_L) = E \ket{\psi}_L$, the second term will go to zero and the output state becomes 
\begin{equation}
E \ket{\psi}_L \ket{0}_A,
\end{equation}
such that if one measures $Z$ on the ancilla they will get the outcome $+1$ (syndrome bit $0$) with certainty. 

If $P ( E \ket{\psi}_L) = - E \ket{\psi}_L$, the first term will go to zero and the output state becomes 
\begin{equation}
E \ket{\psi}_L \ket{1}_A,
\end{equation}
such that a $Z$ measurement performed on the ancilla now gives the outcome $-1$ (syndrome bit $1$) with certainty. 

By performing the above circuit and measuring the ancilla one can therefore determine if the logical state is in the $+1$ or $-1$ eigenspace of the stabilizer $P$. 

This is an example of [generalised measurement](#Generalised_measurement_full_definition_target) and [Naimark’s dilation theorem](#naimark_dilation_theorem). 

<!-- Note, this method of performing measurements only really works for measuring observables in $\mathcal{P}_n$ on stabilizer states. -->

:::{dropdown} Parity Measurements Circuits

When discussing the [2-bit repetition code](#target_error_correction_2_bit_repetition_code) it was noted that the measurement of the stabilizer was akin to performing a parity check on the qubits. Specifically, a logical qubit was encoded into space ${\rm Span}\{ \ket{00}, \ket{11}\}$ such that 
\begin{equation}
\ket{\psi}_L = \alpha \ket{00} + \beta \ket{11}, ~ ~ \vert \alpha \vert^2 + \vert \beta \vert^2=1.
\end{equation}
It was then seen that it was possible to perform error detection on the set of errors $\{\mathbb{I}, X_1, X_2 \}$ by measuring the stabilizer $Z_1 \otimes Z_2$. If $\mathbb{I}$ occurs, the state stays in the code space and measuring the stabilizer gives the output $+1$ (syndrome bit $0$). If either an $X_1$ or $X_2$ occurs, the state is mapped into the space ${\rm Span}\{ \ket{01}, \ket{10} \}$, and a measurement of the stabilizer gives the output $-1$ (syndrome bit $1$).

A simpler circuit can be used for measuring stabilizers that perform a parity check. The circuit for performing the parity check in the 2-bit repetition code is shown in the below figure. 

```{figure} errorCorrectionStabMeasureCircuitParity.png
:alt: 
:class: bg-primary
:width: 600px
:align: center
:target: stab_measure_circuit_target

A circuit that checks the parity of two qubits and stores the result in an ancilla. $L_1$ and $L_2$ are used to label the two physical qubits used to create the single logical qubit. 
```

Firstly, the parity of two bits, $i_1, i_2 \in \{0,1\}$, is given by $i_1 \oplus i_2$. This will be zero if both bits are zero or both bits are one. If the bits differ, it will be one. 

Now, note that the action of a CNOT gate on some arbitrary computational basis state can be written as 
\begin{equation}
C_1X_2 \ket{i_1i_2} = \ket{i_1(i_2 \oplus i_1)}, ~ ~ i_1, i_2~\in~\{0,1\}.
\end{equation}
This works because a CNOT gate applies an $X$ gate to the second qubit if the first qubit is $i_1 = 1$. This $X$ gate will flip the second qubit, which can be done by adding $1$ to it. Hence, if $i_1 = 0$ nothing is added to the second qubit and it remains $i_2$. If $i_1=1$ then $1$ is added to $i_2$, flipping it. 

From here, consider that if it is not known if an error has occurred on an arbitrary qubit encoded into the code space, ${\rm Span}\{\ket{00}, \ket{11}\}$, the state can be written as
\begin{equation}
\alpha \ket{i_1 i_2} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)}.
\end{equation}
The input into the circuit is then 
\begin{align*}
\big( \alpha \ket{i_1 i_2} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \big) \otimes \ket{0}_A.
\end{align*}
The action of the first CNOT gate is then 
\begin{align*}
&C_2X_A \big( \alpha \ket{i_1 i_2} \otimes \ket{0}_A + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{0}_A \big) \\
=&\alpha \ket{i_1 i_2} \otimes \ket{0 \oplus i_2}_A + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{(i_2 \oplus 1)}_A \\
=& \alpha \ket{i_1 i_2} \otimes \ket{i_2} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{(i_2 \oplus 1)}_A,
\end{align*}
as $0 \oplus i_2 = i_2$. The action of the second CNOT gate is then 
\begin{align*}
&C_1X_A \big( \alpha \ket{i_1 i_2} \otimes \ket{i_2} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{(i_2 \oplus 1)}_A \big) \\
=&\alpha \ket{i_1 i_2} \otimes \ket{i_2 \oplus i_1} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{(i_2 \oplus 1) \oplus (i_1 \oplus 1)}_A \\
=& \alpha \ket{i_1 i_2} \otimes \ket{i_2 \oplus i_1} + \beta \ket{(i_1 \oplus 1)(i_2 \oplus 1)} \otimes \ket{i_2 \oplus i_1}_A,
\end{align*}
as $1 \oplus 1 = 0$. Hence, if $Z$ is measured on the computational basis then the parity is output with certainty. 
:::