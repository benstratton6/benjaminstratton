---
title: Subsystem Codes
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
keywords: Quantum Error Correction, Subsystems, Tensor Product. 
abstract: The mathematical formulation of subsystem codes
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

Typically, quantum error correcting codes encode logical information in a [subspace](#vector_subspaces_definition_target) of a larger dimensional [Hilbert space](#hilbert_space_target). Subsystem codes encode the logical information within a tensor factor of a subspace. 

For more on this topic, see:
- [Quantum error correction and fault tolerance: A comprehensive tutorial.](https://doi.org/10.48550/arXiv.2605.29137)
- [Stabilizer Formalism for Operator Quantum Error Correction.](https://doi.org/10.48550/arXiv.quant-ph/0508131)

## Overview

Let $\mathcal{H}_{n} = (\mathbb{C}_2)^{\otimes n}$ be a [Hilbert space](#hilbert_space_target) of $n$-qubits. 

In a subspace code, the logical space would be some $\mathcal{C} \subseteq \mathcal{H}_n$. 

In a subsystem code, the logical space takes the form $\mathcal{C} = \mathcal{H}_L \otimes \mathcal{H}_G$, where the logical information is encoded in the Hilbert space $ \mathcal{H}_L$ and the Hilbert space $\mathcal{H}_G$ is the gauge subsystem. 

The state in the gauge subsystem is allowed to change as long as it does not effect the logical information encoded in $\mathcal{H}_L$.  

If ${\rm dim}(\mathcal{H}_G) = 1$, then a subsystem code becomes a subspace code. Hence, subspace codes are a special case of subsystem codes. 

## Definition 

A $[[n,k,g,d]]$ subsystem code is defined by a decomposition of the $n$ qubit Hilbert space $\mathcal{H}_{n}$ as
\begin{equation}
\mathcal{H}_{n} = \mathcal{C} \oplus \mathcal{C}^{\perp} = \big(\mathcal{H}_L \otimes \mathcal{H}_G \big) \oplus \mathcal{C}^{\perp}, 
\end{equation} 
where: 
- $\mathcal{C}$ is the code space, 
- $\mathcal{H}_L$ is the logical subsystem, with ${\rm dim}(\mathcal{H}_L)=2^k$
- $\mathcal{H}_G$ is the gauge subsystem, with ${\rm dim}(\mathcal{H}_G) = 2^g$. 

Hence, $n$ is the number of physical qubits, $k$ is the number of logical qubits, $g$ is the number of gauge qubits, and $d$ is the distance of the code. 

A subsystem code will be defined via both [stabilizers](#stabilizer_definition_target), $\mathcal{S}$, and a Gauge group, $G$. The [stabilizers](#stabilizer_definition_target) are an Albeian [subgroup](#group_page_subgroup_definition) of the $n$-qubit Pauli-group that does not included $-\mathbb{I}$; the Gauge group is a potentially non-albelian [subgroup](#group_page_subgroup_definition) of the $n$-qubit Pauli-group with [centre](#centre_definition_target) 
\begin{equation}
C(G)= \langle \mathcal{S}, i \mathbb{I} \rangle.
\end{equation}
Elements of $G$ are of the form $\mathbb{I}_L \otimes g_G$, meaning they only act non-trivially on the gauge subsystem. See [](https://doi.org/10.48550/arXiv.quant-ph/0508131) for a proof. 

### Definition With Virtual Paulis

A set of [virtual Paulis](#virtual_paulis_target_palui_group_page) $\big\{X'_j, Z'_j \big\}_{j \in \{1,n\}}$ can be used to [defined a set of stabilizers](#virtual_pauli_definition_of_stabilzer_codes_target) as 
\begin{equation}
\mathcal{S} = \langle Z'_1, Z_2', \ldots Z_m' \rangle,
\end{equation}
where $m = n - k - g$. The gauge group of a subsystem code is then defined as 
\begin{equation}
G = \langle i \mathbb{I}, \mathcal{S}, X'_{m+1}, Z'_{m+1}, X'_{m+2}, Z'_{m+3}, \ldots, X'_{m+g}, Z'_{m+g} \rangle. 
\end{equation}
By design, $\{X'_{m+q}, Z'_{m+q}\}=0~\forall~q \in \{1,g\}$. 

The pairing of the non-commuting Pauli operators $X'_{m+q}$ and $Z'_{m+q}$ is necessary for ensuring the existence of a subsystem structure.

#### Logical Operators

Logical operators are operators that act non-trivially on $\mathcal{H}_L$ whilst preserving the codespace $\mathcal{C}$. They are elements of the normalizer of the stabilizer group that are not in $G$. 

In terms of the virtual Pauli's, the normaliser of the stabilzer group is
\begin{equation}
N(\mathcal{S}) = \langle i \mathbb{I}, \mathcal{S}, Z'_{m+1}, Z'_{m+2}, \ldots, Z'_{n}, X'_{m+1}, X'_{m+2} \ldots, X'_{n} \rangle.
\end{equation}
The logical operators of the subsystem code are then 
\begin{equation}
N(\mathcal{S}) \setminus G = \langle X'_{m+g+1}, Z'_{m+g+1}, X'_{m+g+2}, Z'_{m+g+2}, \ldots, X'_{n}, Z'_{n} \rangle.
\end{equation}
Hence, there are $k$ logical $X$ operators, and $k$ logical $Z$ operators for each of the $k$ logical qubits.  