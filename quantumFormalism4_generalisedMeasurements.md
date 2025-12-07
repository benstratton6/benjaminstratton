---
title: Generalised Measurements  
subject: 
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
keywords: Measurements, eigenvalues, POVMs, Generalised Measurements   
abstract: Measurements in quantum mechanics can be generalised beyond observables through the notion of generalised measurements and POVMs.    
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

## Generalised Measurements  

This section of notes is partly based on content from Chapter 3 of [Resource of the Quantum world](https://doi.org/10.48550/arXiv.2402.05474)

### Definition 
A generalised measurement is a set of $m$ operators, $\{ M_{x} \}_{x=0}^{m-1}$, such that 
(Generalised_measurement_definition_target)=
\begin{equation}
\sum_{x=0}^m M_x^\dagger M_x = \mathbb{I}.
\end{equation}

This condition ensures that the sum of the probabilities of getting the different possible outcomes of the measurement is one. 

### Measuring a Generalised Measurement

Let $\ket{\psi} \in \mathcal{H}$ be some quantum state. 

When the generalised measurement defined by $\{ M_{x} \}_{x=0}^{m-1}$ is applied to the state $\ket{\psi}$ the post measurement state upon getting the outcome $x$, denoted $\ket{\psi_x}$, is  
\begin{equation}
\ket{\psi_x} = \frac{1}{\sqrt{p_x}} M_x \ket{\psi},
\end{equation}
where $p_x$ is the probability of getting the outcome $x$, given by 
\begin{equation}
p_x = \bra{\psi} M_x^\dagger M_x \ket{\psi}.
\end{equation}

If instead one considers a state $\rho \in \mathcal{H}$. 

When the generalised measurement defined by $\{ M_{x} \}_{x=0}^{m-1}$ is applied to the state $ \rho $, the post measurement state upon getting the outcome $x$, denoted $\rho_x$, is  
\begin{equation}
\rho_x = \frac{1}{p_x} M_x \rho M_x^\dagger,
\end{equation}
where $p_x$ is the probability of getting the outcome $x$, given by 
\begin{equation}
p_x = \textrm{tr}\big[ M_x^\dagger M_x\rho \big].
\end{equation}

### Physical Realisation

All generalised measurements can always be produced from the action of a joint unitary on a state and ancilla, followed by a projective measurement on the ancilla. The measurement outcome is given by the output of the projective measurement on the ancilla. Depending on this output, it is then known what the post measurement state is. 

```{figure} quantumFormalism4_generalisedMeasurements_image_1.jpeg
:alt: 
:class: bg-primary
:width: 600px
:align: center
<!-- :target: generalised_Measurements_image_target -->

The orange box represents the generalised measurement. A state, $\ket{\psi} \in \mathcal{H}_{S}$ first has an ancilla, $\ket{0} \in \mathcal{H}_A$, appended. A joint unitary, $U_{SA}$, is then applied on the system and ancilla. A projective measurement is then applied on $A$. The outcome of this measurement then informs the post measurement state in $S$. 
```

### Generalised Measurements as a Channel

It can be seen from the [definition of a generalised measurement](#Generalised_measurement_definition_target) that it is the same definition as the [Kraus decomposition](#Kraus_decomposition_quantum_channel_target) of a quantum channel - a completely positive trace-preserving map. 

Each element of the generalised measurements, $\{ M_{x} \}_{x=0}^{m-1}$, can then be thought to  define a completely positive *trace non-increasing* map on a state. Given a state $ \rho $, the post measurement state is now defined as 
\begin{equation}
\rho_x = M_x \rho M_x^\dagger = \Lambda_x(\rho), 
\end{equation}
where $\Lambda_x(\cdot)$ is a completely positive trace non-increasing map. The sum over all these completely positive trace non-increasing maps will then give a completely positive trace preserving  map,
\begin{equation}
\Lambda = \sum_{x=0}^{m} \Lambda_x,~~\Lambda~\in~{\rm CPTP},
\end{equation}
due to the definition of a generalised measurement. 

In the literature, this is referred to as a [quantum instrument](https://en.wikipedia.org/wiki/Quantum_instrument). Physically, this says that a generalised measurement performed on a state $ \rho $ maps the state to a quantum-classical register where the measurement outcomes are stored in the classical register and the post measurement state in the quantum register. If an outcome $x$ is in the classical register, then $\Lambda_x(\rho)$ is in the quantum register. A quantum instrument, $\mathcal{G}$, is then defined as the map 
\begin{equation}
\mathcal{G}(\rho) = \sum_x \Lambda_x(\rho) \otimes \ket{x}\bra{x}, ~ ~ \sum_x \Lambda_{x} = \Lambda~\in~{\rm CPTP}.
\end{equation}

## POVMs
(POVM_measurement_definition_target)=
A Positive Operator Valued Measure (POVM) is a generalised measurement where one does not care about the post measurement state, only the probability of getting different outcomes. This might be the case because the post measurement states is unimportant for any future use, or, it might be because it physically does not exists, such as when a photon is measured. In this case, the photon is destroyed, leaving no photon for a post measurement state to exist in. 

Hence, rather than considering the set of operators $\{ M_{x} \}_{x=0}^{m-1}$, one can instead consider only the set $\{ T_x = M_x^\dagger M_{x} \}_{x=0}^{m-1}$ which is enough to give the probabilities of the different possible outcomes occurring. However, one loses the ability to calculate the post measurement state.

### Definition 

A POVM is a set of $m$ operators, $\{ T_{x} \}_{x=0}^{m-1}$, such that 
\begin{equation}
\sum_{x=0}^m T_x = \mathbb{I}, ~ ~ \textrm{and} ~ ~ T_x \geq 0~\forall~x.
\end{equation}

The first condition carries from the definition of the generalised measurement and it once again ensures that the sum of the probabilities of getting the different possible outcomes is one. The second condition ensures that all these probabilities are positive.  

### Physical Realisation

All POVM's can be physically realised by just performing the associated generalised measurement and ignoring the post measurement state.   

**Naimark's dilation theorem**

Naimark's dilation theorem states that every POVM can be realised by a projective measurement (the measurement of some [observable](#obersvables_definition_observable_page_target)) on a higher dimensional space. 

Consider a POVM, $\mathcal{T}$, acting on a Hilbert space $\mathcal{H}^{d}$ given by 
\begin{equation}
\mathcal{T} = \{ T_i : T_i \geq 0, \sum_i T_i = \mathbb{I} \}.
\end{equation}

Then there exists a projective measurement 
\begin{equation}
\mathcal{P} = \{ \Pi_i: \Pi_i^2 = \Pi_i,~ \Pi_i \Pi_j = \delta_{ij}\Pi_i, \sum_i \Pi_i = \mathbb{I} \}.
\end{equation}
acting on a Hilbert space $\mathcal{H}^{d'}$, where $d' \geq d$, such that 
\begin{equation}
T_i = V^\dagger \Pi_i V ~ \forall ~i,
\end{equation}
where $V: \mathcal{H}^{d'} \rightarrow \mathcal{H}^{d}$, is an isometry.

This theorem ensures that all POVMs are physically realisable through the measurement of an observable on a higher dimensional space. 


### Properties 

For each generalised measurement there is a unique POVM that corresponds to it. On the other hand, for each POVM there are many possible generalised measurements that correspond to it. 

