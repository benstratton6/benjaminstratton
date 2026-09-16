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

## Definition 

A $[[n,k,g,d]]$ subsystem code is defined by a decomposition of the $n$ qubit Hilbert space $\mathcal{H}_{n}$ as
\begin{equation}
\mathcal{H}_{n} = \mathcal{C} \oplus \mathcal{C}^{\perp} = \big(\mathcal{H}_L \otimes \mathcal{H}_G \big) \oplus \mathcal{C}^{\perp}, 
\end{equation} 
where $\mathcal{C}$ is the code space, $\mathcal{H}_L$ is the logical subsystem, with ${\rm dim}(\mathcal{H}_L)=2^k$, and $\mathcal{H}_G$ is the gauge subsystem, with ${\rm dim}(\mathcal{H}_G) = 2^g$. 

Hence, $n$ is the number of physical qubits, $k$ is the number of logical qubits, $g$ is the number of gauge qubits, and $d$ is the distance of the code. 

A subsystem code will be defined via both [stabilizers](#stabilizer_definition_target), $\mathcal{S}$, and a Gauge group, $G$. The [stabilizers](#stabilizer_definition_target) are an Albeian [subgroup](#group_page_subgroup_definition) of the $n$-qubit Pauli-group that does not included $-\mathbb{I}$; the Gauge group is a [subgroup](#group_page_subgroup_definition) of the $n$-qubit Pauli-group with [centre](#centre_definition_target) 
\begin{equation}
C(G)= \langle \mathcal{S}, i \mathbb{I} \rangle.
\end{equation}

Elements of $G$ need not be abelian. Moreover, the above definition states that all elements of the gauge group that commute with all other elements of the gauge group must be a stabilizer.  and they act on the code space as $\mathbb{I}_L \otimes g_G$, meaning that they act trivially on the logical subsystem and with $g$ on the gauge system. 