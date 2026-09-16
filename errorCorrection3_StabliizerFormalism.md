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
(stabilizer_definition_target)=
\begin{equation}
\mathcal{S} = \big\{ P_i \in \mathcal{P}_n: P_i \ket{\psi}_L = \ket{\psi}_L~\forall~\ket{\psi}_L \wedge [P_i, P_j] = 0 ~ \forall ~ (i,j) \big\},
\end{equation}
such that $-\mathbb{I} \notin \mathcal{S}$. The stabilizers are therefore an [Abelian subgroup](#albelian_group_definition) of the $n$-qubit Pauli-group, $\mathcal{P}_n$, such that all logical states (states in the code space) are $(+1)$ eigenstates of each stabilizer, that does not contain the negative identity operator. 

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
P_i = \Pi^i_{+} - \Pi^i_{-},
\end{equation}
where $\Pi^i_{+}$ is the projector onto the $+1$ eigenspace of $P_i$ and $\Pi^i_{-}$ the projector onto the $-1$ eigenspace of $P_i$. One can then defined the code space via the projector
\begin{equation}
\Pi_{\mathfrak{C}_L} = \cap_{i=0}^{\vert \mathcal{S} \vert} \Pi^i_{+},
\end{equation}
which is the projector onto the intersection of all the positive eigenspaces of the stabilizers. 

The intersection of all the different combinations of the positive and negative eigenspaces of the stabilizers are all pairwise orthogonal, and they define each of the orthogonal subspaces of the QEC code.  

An error that maps the code space to one of these orthogonal subspaces can therefore be detected by measuring the observable who's eigenspaces are exactly these orthogonal subspaces.  

### Stabilizer Generators 

The stabilizers form an [(abelian)](#albelian_group_definition) subgroup of the $n$-qubit Pauli-group. Hence, they can be represented in terms of a set of [independent generators](#group_generators_definition) [💭](#size_of_abelian_groups).

The code space of a stabilizer code can then be defined from the stabilizer generators only. 

To see this, let $\mathcal{S} = \langle \tilde{S} \rangle$ where $\tilde{S} = \big\{ S_1, S_2, \ldots, S_m \big\}$ for $S_i \in \mathcal{P}_n \forall~i$. If 
\begin{equation}
S_i \vert \psi \rangle_L = \vert \psi \rangle_L ~ ~ {\rm and} ~ ~ S_j \vert \psi \rangle_L = \vert \psi \rangle_L
\end{equation}
then 
\begin{equation}
S_i S_j \vert \psi \rangle_L = S_i \vert \psi \rangle_L = \vert \psi \rangle_L.
\end{equation}
Hence, any state in the $+1$ eigenspace of both $S_i$ and $S_j$ is also in the $+1$ eigenspace of their product $S_iS_j$. Therefore, the simultaneous $+1$ eigenspace of the generators is the simultaneous $+1$ eigenspace of the stabilizers, and hence, is the code space. 

Moreover, only the stabilizer generators need to be measured, as the measurements of all other stabilizers can be calculated in post-processing from the measurement outcomes of the generators. 

:::{dropdown} Proof

Let $S_i$ and $S_j$ be stabilizer generators, such that $S_i, S_j \in \mathcal{P}_n$ and $[S_i, S_j]=0$. Moreover, let
\begin{equation}
S_i \vert \psi \rangle_L = \alpha \vert \psi \rangle_L ~ ~ {\rm and} ~ ~ S_j \vert \psi \rangle_L = \beta \vert \psi \rangle_L,
\end{equation}
where $\alpha, \beta \in \{0,1\}$. 

The eigenvalue of the stabilizer $S_iS_j=S_jS_i$ is then 
\begin{align*}
S_iS_j \vert \psi \rangle_L &= S_i (\beta \vert \psi \rangle_L) \\
&= \beta (S_i \vert \psi \rangle_L) \\
&= \beta \alpha \vert \psi \rangle_L.
\end{align*}

Hence, the eigenvalue of $S_iS_j$ is just the product of the eigenvalues of $S_i$ and $S_j$.
:::

#### Number of Logical Qubits 

If a code on $n$ physical qubits has $m$ stabilizer generators, then the number of logical qubits, $k$, is given by 
\begin{equation}
k = n - m.
\end{equation}

:::{dropdown} Proof

Each stabilizer generator is an element of the Pauli-group, meaning its $+1$ and $-1$ eigenspaces [evenly split the Hilbert space](#eigenvalues_of_pauli_strings_target). 

Given a Hilbert space of $n$-qubits, its dimension is $2^n$. The dimension of the $+1$ eigenspace of a stabilizer generator is therefore $2^n/2 = 2^{n-1}$. Hence, the constraint of a stabilizer generator can be thought of as _removing one qubit_ from the Hilbert space. 

We now aim to show that each additional stabilizer generator removes one further qubit from the Hilbert space. 

Let $S_i$ and $S_j$ be stabilizer generators, such that $S_i, S_j \in \mathcal{P}_n$ and $[S_i, S_j]=0$. Both $S_i$ and $S_j$ can be decomposed in their eigenbasis as 
\begin{align*}
S_i &= \Pi^i_{+} - \Pi^i_{-} \\
S_j &= \Pi^j_{+} - \Pi^j_{-},
\end{align*}
where
\begin{equation}
\Pi^\alpha_{\pm} = \frac{\mathbb{I} \pm S_\alpha}{2}.
\end{equation}
As $[S_i, S_j]=0$, the projector onto simultaneous $+1$ eigenspace is given by 
\begin{equation}
\Pi^j_{+}\Pi^i_{+} = \Pi^i_{+}\Pi^j_{+}.
\end{equation} 
The dimension of a projector is then given by its trace, meaning the dimension of this projector is therefore 
\begin{align*} 
{\rm tr}\big[ \Pi^j_{+}\Pi^i_{+} \big] &= {\rm tr}\bigg[ \bigg( \frac{\mathbb{I} + S_j}{2} \bigg) \bigg( \frac{\mathbb{I} + S_i}{2} \bigg) \bigg] \\
&= \frac{1}{4} \textrm{tr} \big[ \mathbb{I} + S_i + S_j + S_j S_i \big] \\
&= \frac{2^n}{4},
\end{align*}
where we have used the fact that the trace of non-identity elements of the Pauli-group is zero, and $S_i S_j \neq \mathbb{I}$ as $S_i$ and $S_j$ are independent stabilizer generators. 

Hence, the addition of another constraint of a stabilizer generator half's the size of the simultaneous $+1$ eigenspace.

This can be generalized to $r$ independent commuting stabilizers, with each additional stabilizer generator halving the size of the simultaneous $+1$ eigenspace. Therefore, given $m$ stabilizer generators, the size of the simultaneous $+1$ eigenspace is 
\begin{equation}
\frac{2^n}{2^m} = 2^{n-m},
\end{equation}
which is a space capable of encoding $k=n-m$ qubits. 
:::

### Logical Operators

A logical operator is an operator that acts on encoded states in the same way as it would act on a physical state. This means all expected commutations relations must hold. 

The possible logical operators of a stabilizer code are
\begin{equation}
N(\mathcal{S}) \setminus \mathcal{S},
\end{equation}
where $N(\mathcal{S})$ is the [normalizer](#normalizer_definition_target) of $\mathcal{S}$. 

All elements of the Pauli-group commute or anti-commute, and the stabilizer generators never include $-\mathbb{I}$. Hence, the normalizer of $\mathcal{S}$ is equal to the [centralizer](#centralizer_definition_target) of $S$.

The possible logical operators are therefore the elements of the Pauli-group that mutually commute with all elements of $\mathcal{S}$ but are not in $\mathcal{S}$. 

This definition ensures that states acted upon by a logical operator remain within the code space. 
:::{dropdown} Proof

Let $\vert \psi \rangle_L$ be an arbitrary state in the code space i.e., the $+1$ eigenspace of all stabilizers $\mathcal{S}$, and let $S \in \mathcal{S}$. Hence, $S \vert \psi \rangle_L = \vert \psi \rangle_L$. 

Now, let $U \in N(\mathcal{S}) \setminus \mathcal{S}$. We now aim to show that $U \vert \psi \rangle_L$ remains inside the code space. 

This is actually easy to see as 
\begin{align*}
S(U \vert \psi \rangle_L) &= U (S \vert \psi \rangle_L) \\
&= U \vert \psi \rangle_L,
\end{align*}  
as $[U,S]=0$. Hence, if $\vert \psi \rangle_L$ was in the $+1$ eigenspace of $S$, so is $U \vert \psi \rangle_L$. 

The above was true for an arbitrary stabilizer and, given all stabilizers commute, will generalize to the application of any number of stabilizers. 

Hence, if $\vert \psi \rangle_L$ is in the simultaneous $+1$ eigenspace of all stabilizers, then so is $U \vert \psi \rangle_L$.   
::: 

#### Uniqueness 

Logical operators are not unique, as any logical operator multiplied by a stabilizer will perform the same logical operation. 

To see this, let $S \in \mathcal{S}$, $U \in N(\mathcal{S}) \setminus S$ and assume $\vert \psi \rangle_L$ is an arbitrary state in the code space. Then
\begin{equation}
U (S \vert \psi \rangle_L) = U \vert \psi \rangle_L,
\end{equation}
meaning $US$ and $U$ have the same effect on the logical state. 

To capture this, logical operators are formally represented by [cosets](#group_theory_page_cosets_definition) of $\mathcal{S}$ insides $N(\mathcal{S})$. Given a $U \in N(\mathcal{H})$, the left [coset](#group_theory_page_cosets_definition) 
\begin{equation}
\big\{ US : S \in \mathcal{S} \big\},
\end{equation}
forms a set of equivalent logical operators. If $U \in \mathcal{S}$, then the coset is equal to $\mathcal{S}$ with the logical operator being the identity.  

As a result of this, logical operators are studied via the [quotient group](#quotient_group_definition_target) of $N(\mathcal{S})$ with respect to $S$, i.e., $N(\mathcal{S}) / \mathcal{S}$. This [quotient group](#quotient_group_definition_target) combines together all the operators in $N(\mathcal{S})$ that perform the same logical operator and treats them equivalently. Relationships between these set of operators (that perform the same logical operator) can then be studied.  

#### Code Distance

The distance of an error correcting code is the minimum number of errors that can occur without the error being detected by the code. 

For a stabilizer code, the distance is given by the minimum weight of an element in $N(\mathcal{S}) \setminus \mathcal{S}$. 

:::{dropdown} Justification

Errors are considered to be individual Pauli-errors acting on the qubits, with the weight of a Pauli-string - the number of qubits on which the string acts non-trivially - corresponding to the number of errors that given Pauli-string will have caused. For example, 
\begin{equation}
X_1X_2X_5
\end{equation} 
corresponds to an $X$ error on qubits $1,2$ and $5$. That is $3$ errors, equal to the weight of the string.

Elements of $N(\mathcal{S}) \setminus \mathcal{S}$ are the logical operators of the stabilizer code i.e., the Pauli-string that keep states within the code space but act non-trivially on them. 

Hence, if an error $E \in N(\mathcal{S}) \setminus \mathcal{S}$ occurs, it will go undetected, as the state will remain in the code space but an unknown operation will have been applied. 

Therefore, the minimum weight of an element in $N(\mathcal{S}) \setminus \mathcal{S}$ will be the distance of the code. 
:::

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

(virtual_pauli_definition_of_stabilzer_codes_target)=
### Virtual Paulis

Stabilzers can also be formalised in terms of [virtual Paulis](#virtual_paulis_target_palui_group_page). 

Here, $2n$ elements of $\mathcal{P}_n$ are choosen, $\{X'_j, Z'_j \}_{j \in \{1,n\}}$, such that the [single-qubit commutation relations](#single_qubit_pauli_realtions) are obeyed as expected. 

The stabilzer group can then be choosen to be 
\begin{equation}
\mathcal{S} = \langle Z'_1, Z_2', \ldots Z_m' \rangle,
\end{equation}
where $m \leq n$. These are independent, mutually commuting, and do not contain $-\mathbb{I}$. 

The normaliser of this stabilzer group is then 
\begin{equation}
N(\mathcal{S}) = \langle i\mathbb{I}, \mathcal{S}, Z'_{m+1}, Z'_{m+2}, \ldots, Z'_{n}, X'_{m+1}, X'_{m+2} \ldots, X'_{n} \rangle,
\end{equation}
which are the logical operators of the code. 

:::{dropdown} More Details

As detailed [here](#more_detail_virtual_paulis_target), the eigenbasis of these stabilzers can be labeled by bit-strings $\bm{b} = b_1b_2...b_n \in \{0,1\}^n$, such that 
\begin{align*}
Z'_j \ket{b_1b_2b_3 \ldots b_n} &= (-1)^{b_j} \ket{b_1b_2b_3 \ldots b_n}, \\
X'_j \ket{b_1b_2b_3 \ldots b_n} &= (-1)^{b_j} \ket{b_1b_2b_3 \ldots b_{j-1}(b_j \oplus 1)b_{j+1} \ldots b_n}.
\end{align*}
As the code space is defined as the $+1$ eigenspace of the stabilzers, using this basis the code space can be defined as the space spanned by the states
\begin{equation}
\big\{ \ket{\bm{0}_m \bm{a}_{n-m}} : a \in \{0,1\}^{n-m} \big\}
\end{equation}
where $\bm{0}_m$ is the zero bit-string of length $m$.

Consistency check: 
- There are $2^{n-m}$ possible code-words, meaning $k=n-m$ qubits can be encoded. 
- Elements in the normaliser act only on the final $n-m$ bits, and hence manipulate the code words (and hence the logical information) without effecting the first $m$ bits, keeping the state in the code space. 

If a correctable error acts on the encoded state, it will map the first $m$ zeros bits to some other $m$ bit-string. This will then be the syndrome of the error correcting code, which will be extracted when the $m$ stabilzer generators are measured. 
:::