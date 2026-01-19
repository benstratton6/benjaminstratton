---
title: Resource Theory of Non-stabilizerness
subject: 
subtitle: 
# short_title: How to MyST
authors:
  - name: Benjamin Stratton
    # affiliations:
    #   - Executable Books
    #   - Curvenote
    orcid: 0009-0001-2746-3668
    email: ben.stratton@bristol.ac.uk
license: CC-BY-4.0
keywords: Resource Theories, Magic, Non-stabilizerness, Quantum Computation. 
abstract: An overview of the resource theory of Non-stabilizerness (magic) for fault tolerent quantum computation.
exports:
  - format: pdf
    template: physical_review_journals
    article_type: Report
--- 

## Overview

Not all quantum computations are hard. Given access to only stabilizer states, Clifford unitaries, and computational basis measurements, all implementable operations — the so called _stabilizer operations_ — can be simulated efficiently on a classical computer [](https://doi.org/10.48550/arXiv.quant-ph/9705052) [](https://doi.org/10.48550/arXiv.quant-ph/0406196) [](https://doi.org/10.48550/arXiv.1307.7171). Thankfully for the field of quantum computation, these operations are also not [universal](#universal). However, the set of stabilizer operations are practically significant, as they can typically be implemented easily (transversely) in fault-tolerant quantum computing frameworks [](#https://doi.org/10.48550/arXiv.0908.0836), and stabilizer states are essential to most error correction protocols. Therefore, whilst stabilizer operations alone are not able to realise quantum advantage, they are operationally favourable. 

To perform non-classically-simulable quantum operations, and ultimately achieve universal quantum computation, one must be able to perform non-stabilizer operations. Fortunately, these can be achieved via stabilizer operations if they are supplemented with non-stabilizer states [](https://doi.org/10.48550/arXiv.quant-ph/0403025); however, non-stabilizer states cannot be generated from stabilizer operations alone [](https://doi.org/10.48550/arXiv.1307.7171). Such a setting aligns with that of a [quantum resource theory](#resource_theroies_introduction_page_target). Here, stabilizer operations are regarded as the allowed operations and the stabilizer states as the free states. Access to non-free — or resourceful — non-stabilizer states then enables operations outside of the set of allowed operations to be implemented. In the case of qubits, if one has access to magic states, they are able to perform universal quantum computation using stabilizer operations.

Here we will focus on the qubits, but the resource theory of non-stabilizerness can also be defined for d-dimensional systems. 

## Framework

Let $\mathcal{H}_{n}=(\mathbb{C}^{2})^{\otimes n}$ be the $n$-qubit Hilbert space of dimension $d=2^n$.  

Let $\mathcal{P}_{n}$ be the set of $n$-qubit Pauli strings — these are all the $n$-fold tensor product of the qubit Pauli operators $\mathbb{I}, X, Y, Z$, where $\vert \mathcal{P}_n \vert = 4^{n}$.
