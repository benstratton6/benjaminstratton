---
title: QEC Structure 
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
abstract: A high level overview of underlying structure of quantum error correcting codes.    
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(QEC_Structure_page)=
A quantum error correcting code works by first encoding a $k$-dimensional logical state into a subspace of some $d$-dimensional Hilbert space. It is then assumed that an error from some pre-determined set of errors occurs on this state. A measurement can then be designed which is able to reveal which of these errors has occurred, without any information about the logical state being discovered.

To illustrate this idea, an error correcting code able to correct a single error is first designed,before being extended to multiple errors.  

### Single Error Code

An error correcting code is defined by first establishing a set of code words. These are typically a set of orthogonal pure states $ \{ \ket{i} \}_{i=0}^{k}$, such that $\braket{i | j}=\delta_{i,j}$. The code space, $\mathfrak{C}_L$, is then the subspace of the full Hilbert space, $\mathcal{H}$, spanned by the set of code words,
\begin{equation}
\mathfrak{C}_L = { \rm span }\big\{ \{\ket{i}\}_{i=0}^k \big\} \subsetneq \mathcal{H}.
\end{equation}
The logical state is then some state encoded within this code space, $\ket{\psi}_L \in \mathfrak{C}_L$. We define $\Pi_L$ to be the projector onto the code space,
\begin{equation}
\Pi_L = \sum_{i=0}^k \vert i \rangle \langle i \vert.
\end{equation}  

If some unitary error, $U$, acts on the logical state, the state will be mapped to the space spanned by $U$ acting on the code words,
\begin{equation}
U \ket{\psi}_L \in {\rm Span} \big\{ \{ U \ket{i} \}_{i=0}^{N} \big\} = \mathfrak{C}_U \subseteq \mathcal{H},
\end{equation}
where we have defined this subspace to be $\mathfrak{C}_U$, and the projector onto the space is 
\begin{equation}
\Pi_U = U \Pi_L U^\dagger = \sum_{i=0}^k U \vert i \rangle \langle i \vert U^\dagger.
\end{equation}
The goal of the simplest imaginable error correcting code is then to (a) determine which of the channels $\mathbb{I}$ or $U$ has been applied to the logical state without (b) disturbing the logical state and hence destroying the encoded information. 

Criteria (a) can be considered as an example of quantum channel discrimination, where the logical state is the reference state, with the added constraint of criteria (b). 

:::{dropdown} Error Correction as Quantum Channel Discrimination

In the task of quantum channel discrimination one considers two parties, Alice and a referee. The referee has some reference state, $\rho_R$, and a predetermined set of quantum channels $\{ \mathcal{E}_i \}_{i=0}^{M}$. Both the reference state and the set of quantum channels are known to Alice.  

The referee chooses an index $j \in [0,M]$ and then applies the channel $\mathcal{E}_j \in \{ \mathcal{E}_i \}_{i=0}^{M}$ to the reference state. The referee then sends the state $\mathcal{E}_j(\rho_R)$ to Alice. Alice makes a measurement on the state with the intention of identify the channel the referee applied. The ultimate output of the measurement will therefore be some index $k \in [0, M]$, such that if $k=j$ Alice has succeed in the task and if $k \neq j$ she has failed.

```{figure} error_correction_EC_as_channel_discrimination.png
:alt: 
:class: bg-primary
:width: 600px
:align: center
:target: quantum_channel_discrimination

A schematic of a quantum channel discrimination task. R and A are the referee and Alice respectively. The referee applies a channel from a predetermined set to the reference state and then sends it to Alice. Alice performs a measurement on the state and aims to identify which channel the referee applied. 

```

With some added constraints, error correction can be reframed as a quantum channel discrimination task. The reference state is no-longer a predetermined state but rather an arbitrary state within some predetermined subspace. The referee is then the noise, with it being assumed that the noise is restricted to some likely set of possible channels. Finally, Alice is the decoder of the error correction protocol aiming to identify which error has occurred.  

The major addition to quantum error correction is the need for the logical information encoded into the subspace to not be disturbed by the measurement made by Alice (the decoder). Practically, this means a restriction on the measurements Alice is allowed to perform.   

See the [Quantum State Discrimination](#quantum_state_discrimination_task) page for more details on this task

:::

It is a well known result in quantum information theory that [for two quantum states to be deterministically distinguishable they must be orthogonal](#state_discrimination_deterministic). Here, we are not concerned with specific states, but rather arbitary states encoded into subspaces. However, the result instead just applies to the subspaces. Hence, it is only possible to deterministically determine if $\mathbb{I}$ or $U$ has been applied to the logical state if 
\begin{equation}
\Pi_{L} \Pi_{U} = 0,
\end{equation}
meaning that for any arbitrary state $\ket{\psi}_L \in \mathfrak{C}_L$, it is the case that $\bra{\psi}_L U \ket{\psi}_L=0$. 

If this first condition is met it is always the case that one can find a projector $\Pi_R$, such that 
\begin{equation}
\Pi_L + \Pi_U + \Pi_R = \mathbb{I}, 
\end{equation}
where $\Pi_R$ is the projector onto the reminder of the Hilbert space not covered by $\Pi_L$ and $\Pi_U$. This will defined a subspace orthogonal to both $\mathfrak{C}_L$ and $\mathfrak{C}_U$ and is simply given by $\Pi_R = \mathbb{I} - \Pi_L - \Pi_U$. From here, one can then defined an observable
\begin{equation}
O = \lambda_L \Pi_L + \lambda_U \Pi_U + \lambda_R \Pi_R,
\end{equation}
that can be seen to fulfil both criteria (a) and (b). It fulfils (a) as if $\mathbb{I}$ has been applied (no error) then 
\begin{align*}
P(\lambda_L \vert \ket{\psi}_L) &= {\rm tr} \big[ \Pi_L \vert \psi \rangle \langle \psi \vert_L] = 1 \\
P(\lambda_U \vert \ket{\psi}_L) &= {\rm tr} \big[ \Pi_U \vert \psi \rangle \langle \psi \vert_L] = 0 \\
P(\lambda_R \vert \ket{\psi}_L) &= {\rm tr} \big[ \Pi_R \vert \psi \rangle \langle \psi \vert_L] = 0,
\end{align*}
meaning one gets the outcome $\lambda_L$ with certainty. If instead $U$ has been applied then 
\begin{align*}
P(\lambda_L \vert ~ U \ket{\psi}_L) &= {\rm tr} \big[ \Pi_L ~ (U\vert \psi \rangle \langle \psi \vert_L U^\dagger)] = 0 \\
P(\lambda_U \vert ~ U \ket{\psi}_L) &= {\rm tr} \big[ \Pi_U ~(U\vert \psi \rangle \langle \psi \vert_L U^\dagger)] = 1 \\
P(\lambda_R \vert ~ U \ket{\psi}_L) &= {\rm tr} \big[ \Pi_R ~(U\vert \psi \rangle \langle \psi \vert_L U^\dagger)] = 0,
\end{align*}
meaning one gets the outcome $\lambda_U$ with certainty. The observable $O$ therefore allows one to determine which error has occurred with certainty. It fulfils (b) as the
\begin{align*}
\Pi_L \vert \psi \rangle \langle \psi \vert_L \Pi_L &= \vert \psi \rangle \langle \psi \vert_L, \\
\Pi_U (U\vert \psi \rangle \langle \psi \vert_L U^\dagger) \Pi_U &= U\vert \psi \rangle \langle \psi \vert_L U^\dagger,
\end{align*} 
meaning the states remain unchanged after the measurements. 

The error correcting code can be summarised as follows: if the errors that can occur are $\{ \mathbb{I}, U \}$ and the code space is $\mathfrak{C}_L$, then measure the observable $O$ and if the outcome is $\lambda_L$ do nothing, if it is $\lambda_U$ apply $U^\dagger$. 

### Multiple Errors

The logic above can be easily expanded to multiple errors. Assume the set of possible errors is $\{U_i\}_{i=0}^M$, where $U_0=\mathbb{I}$. Each error must then map the code space to an orthogonal subspace such that 
\begin{equation}
\Pi_{U_j} \Pi_{U_k} = \delta_{jk} \Pi_{U_j}.
\end{equation}

#### Correctable Errors 

A set of unitary errors $\{ U_i \}_i$, such that all elements of the set 
\begin{equation}
\big\{ U_i \Pi_L U_i^\dagger \big\}_i,
\end{equation}
are pairwise orthogonal, can therefore be corrected by measuring the non-degenerate operator 
\begin{equation}
O = \sum \lambda_i (U_i \Pi_L U_i^\dagger).
\end{equation}
Given an initial logical state $\vert \psi \rangle_L$, if one gets the measurement outcome $\lambda_i$ they known they have the state $U_i \vert \psi \rangle_L$. Hence, by applying the unitary $U_i$ they return the logical state without disturbing the encoded information. 

#### Uncorrectable Errors 

Now, imagine there exists another unitary error $V$, such that 
\begin{equation}
V \Pi_L V^\dagger = U_j \Pi_L U_j.
\end{equation}
This means that both the errors $U_j$ and $V$ map the code space to the same subspace. If one now measures $O$ and gets the outcome $\lambda_j$, they will not be able to tell if the error $U_j$ or $V$ has occurred. They will be able to detect the presence of an error, but not necessarily correct it. 

Instead, imagine there exists another error that maps the logical space to a subspace that is partly supported in $U_i \Pi_L U_i$ and partly support in $U_j \Pi_L U_j$. A measurement of $O$ will project the state into either the $U_i \Pi_L U_i$ subspace or the $U_j \Pi_L U_j$. This will alter the logical information in a way that is not recoverable based only the output eigenvalue from measuring $O$. Hence, such errors are not correctable. 

### Conclusion

To design an error correcting code for a set of errors, one must be able to find a code space which is mapped to orthogonal subspaces under the action of each error. By measuring the non-degenerate operator with eigenspaces of these orthogonal subspaces, these errors can be corrected.   

