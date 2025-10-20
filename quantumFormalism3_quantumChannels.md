---
title: Quantum Channels
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
keywords: Dynamics, Channels, Evolution, Positive, Trace Preserving.   
abstract: The details of how the dynamics of quantum states are modelled.    
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(quantum_channel_page_target)=
## Definition 

A quantum channel is a linear, completely positive, trace-preserving map (from the set of density operators to itself). 

A channel mapping from states in an input Hilbert space $\mathcal{H}_{in}$ to an output Hilbert space $\mathcal{H}_{out}$ is denoted as 
\begin{equation}
\mathcal{E}: \mathcal{H}_{in} \rightarrow \mathcal{H}_{out}
\end{equation}

A quantum channel is a more general notion of evolution then that captured via the Schrödinger equation and unitary dynamics as it models interactions with the environment. Unitary dynamics are subset of quantum channels. 

### Linear 

A map, $\mathcal{E}$, is linear if 
\begin{equation}
\mathcal{E}(\rho + \sigma) = \mathcal{E}(\rho) + \mathcal{E}(\sigma)
\end{equation}

### Positive 

A linear map, $\mathcal{E}$, is positive if it maps positive elements to positive elements,
\begin{equation}
\rho \geq 0 \implies \mathcal{E}(\rho) \geq 0.
\end{equation} 


### Completely Positive   

A linear map, $\mathcal{E}$, is completely positive if it remains a positive map when embedded into a high dimensional space,
\begin{equation}
\rho \geq 0 \implies (\mathcal{E} \otimes \mathcal{I}) (\rho) \geq 0,
\end{equation} 
where $\mathcal{I}$ is the identity channel on an arbitrarily large ancilla. 

This additional restriction is needed to ensure that acting that map on part of a larger, potentially entangled state, still outputs a physical quantum state. 

This ensure that all operators output from a channel remain positive semi-definite. 

### Trace-preserving

A map, $\mathcal{E}$, is trace preserving if 
\begin{equation}
\textrm{tr} \big[ \mathcal{E}(\rho) \big] = 1,
\end{equation}
for all $\rho \in \mathcal{H}_{in}$, where $\rho$ is a valid density operator, $ \textrm{tr} \big[ \rho \big] = 1, \rho \geq 0$. 

This ensure that all operators output from a channel still have trace one.

## Channel Descriptions

There are multiple different ways to represent a quantum channel. Each different channel description can be used whenever useful. 

::::{tab-set}
:::{tab-item} Stinespring Dilation
:sync: tab1

Let $\mathcal{E}: \mathcal{H}_{S} \rightarrow \mathcal{H}_{S'}$ be a quantum channel and $\rho~\in~\mathcal{H}_{S}$. 

There exists a state, $\tau_{E}~\in~\mathcal{H}_{E}$, and isometry, $U_{SE}$, such that 
\begin{equation}
\mathcal{E}(\rho) = \textrm{tr}_{E} \big[ U_{SE}(\rho_{S} \otimes \tau_{E}) U_{SE}^{\dagger} \big],
\end{equation}
where the subscript $S$ and $E$ mean system and environment respectively.

The Stinespring dilation says that all channels can be consider unitary with respect to a higher dimensional space. That is, all channels are the interaction of $\rho$ and some environment state, $\tau$ under a global unitary. 

**Properties**

- $\textrm{dim} ~ \tau_{E} \leq d^{2}$ where $\textrm{dim} ~ \rho = d$
- Tracing out the system instead of the enviroment gives the complementary, $\mathcal{E}^{c}$, which can be thought as the channel from the perspective of the environment,
\begin{equation}
\mathcal{E}^{c}(\rho) = \textrm{tr}_{S} \big[ U_{SE}(\rho_{S} \otimes \tau_{E}) U_{SE}^{\dagger} \big].
\end{equation}

:::
:::{tab-item} Kraus Decomposition 
:sync: tab2

Let $\mathcal{E}: \mathcal{H}_{S} \rightarrow \mathcal{H}_{S'}$ be a quantum channel and $\rho~\in~\mathcal{H}_{S}$
(Kraus_decomposition_quantum_channel_target)=
There exists a set of $M$ operators $\{ K_{i} \}_{i=1}^{M}$ such that
\begin{equation}
\mathcal{E}(\rho) = \sum_{i=1}^{M} K_{i} \rho K_{i}^{\dagger},
\end{equation}
where 
\begin{equation}
\sum_{i=1}^{M} K_{i}^{\dagger}K_{i} = \mathbb{I}.
\end{equation}

This condition ensures that the quantum channel is trace preserving. 

The Kraus decomposition allows one to apply channels without having to consider the environment. 

**Properties** 
- The Kraus decomposition is not unique. Although, if there are two sets of operators that both describe the same channel, those sets of operators are unitarily equivalent. 
- $M \leq \dim \mathcal{H}_S \times \dim \mathcal{H}_{S'}$, meaning the number of operators needed for the Kraus decomposition is upper-bounded by the product of the dimensions of the input and output spaces. 

:::
:::{tab-item} Choi-Jamiolkowski isomorphism
:sync: tab3

Let $\mathcal{E}: \mathcal{H}_{S} \rightarrow \mathcal{H}_{S'}$ be a quantum channel,$~\rho~\in~\mathcal{H}_{S}$ be a state, and $\ket{\Phi}_{SS}~\in~\mathcal{H}_{S} \otimes \mathcal{H}_{S}$ a full [Schmit rank state](https://en.wikipedia.org/wiki/Schmidt_decomposition) with $\textrm{dim} ~ \mathcal{H}_{S} \approx \textrm{dim} ~ \mathcal{H}_{S'}$. 

 The Choi-Jamiolkowski isomorphism ([](https://doi.org/10.1016/0034-4877(72)90011-0), [](https://doi.org/10.1016/0024-3795(75)90075-0)) is a linear mapping between quantum channels and bipartite quantum states defined by
(choi_state_target_quantum_channels_page)=
\begin{equation}
    \mathcal{J}^{\mathcal{E}}_{\rm S'S} = (\mathcal{N}_{\rm S} \otimes \mathcal{I}_{\rm S}) \big( \ket{\Phi}\bra{\Phi}_{\rm SS} \big)~\in~\mathcal{H}_{S'} \otimes \mathcal{H}_{S}, 
\end{equation}
where $\mathcal{I}_{\rm S}$ is an identity channel acting on $\mathcal{H}_{S}$.

Typically, the full Schmit rank state state is taken to be a maximally entangled state in a fixed orthonormal basis, 
\begin{equation}
\ket{\Phi}_{AB} = \frac{1}{\sqrt{d}} \sum_{i=0}^{d-1} \ket{i}_{A} \ket{i}_{B}.
\end{equation}

From the Choi-state, the action of $\mathcal{E}$ on a state $ \rho $ can be recovered as 
\begin{equation}
\mathcal{E}(\rho) = d ~ \textrm{tr}_{\rm S}\left[ \left(\mathbb{I}_{\rm S} \otimes \rho^{t}\right) \mathcal{J}^{\mathcal{N}}_{\rm S'S} \right],
\end{equation}
where $(\cdot)^{t}$ is the transpose operation in the given fixed basis of the full Schmit rank state and $ \mathbb{I}_{\rm S} $ is the identity operator on $\mathcal{H}_{S}$. 

:::
::::

## Useful Channels 

::::{tab-set}
:::{tab-item} Dephasing Channel
:sync: tab4

**Qubits**

Let $ \rho \in \mathcal{H}^2$. The dephasing channel acting on $ \rho $ is given by 
\begin{equation}
\mathcal{D}^{\textrm{ph}}_p(\rho) = p \rho + (1-p) \sum_{n} \ket{n}\bra{n} \rho \ket{n}\bra{n}.
\end{equation} 

With respect to the standard basis this becomes 
\begin{equation}
\mathcal{D}^{\textrm{ph}}_p(\rho) = p \rho + (1-p) \bigg( \ket{0}\bra{0} \rho \ket{0}\bra{0} + \ket{1}\bra{1} \rho \ket{1}\bra{1} \bigg)
\end{equation} 

1. The *Kraus operators* are 
\begin{align*}
K_0 &= \sqrt{ 1 - p} \mathbb{I}, ~ ~ K_1 = \sqrt{ p } \ket{0}\bra{0}, ~ ~ K_2 = \sqrt{ p } \ket{1}\bra{1}.
\end{align*}

2. The *Choi-state* is
\begin{equation}

\mathcal{J}^{\textrm{ph}} = \frac{1}{2}(1+p) \ket{\Phi^+_{00}} \bra{\Phi^+_{00}} + \frac{1}{2}(1-p) \ket{\Phi^+_{01}} \bra{\Phi^+_{01}},

\end{equation}
where 
\begin{align*}

\ket{\Phi_{00}^{+}} &= \frac{\ket{0}\ket{0}+\ket{1} \ket{1}}{\sqrt{2}}, \\
\ket{\Phi_{01}^{+}} &= \frac{\ket{0}\ket{0}-\ket{1} \ket{1}}{\sqrt{2}}.

\end{align*}

**d-dimensional**

The d-dimensional dephasing channel has Choi-state:
\begin{equation}
 \mathcal{J}^{\textrm{ph}} = \alpha \vert \Phi_{00}^{+} \rangle \langle \Phi_{00}^{+} \vert + \frac{(1-\alpha)}{d-1} \sum_{c=1}^{d-1} \vert \Phi_{0c}^{+} \rangle \langle \Phi_{0c}^{+} \vert,
\end{equation}
where $\alpha=(p+1)/d$ and $\ket{\Phi_{ab}^+} = (\mathbb{I} \otimes W_{ab}) \ket{\Phi_{00}^+}$ and $W_{ab}$ are the [Heisenberg-Weyl operators](#Generating_Maximally_Entangled_Basis_target).

:::{dropdown} Proof
Using the definition of the Choi-state, it can be seen that the Choi-state of a dephasing channel, $\mathcal{D}^{\rm ph}_{p}(\cdot)$, is given by
\begin{align*}
     \mathcal{J}^{\textrm{ph}} &\coloneqq (\mathcal{D}^{\rm ph}_{p}(\cdot) \otimes \mathcal{I}) \vert \Phi_{00}^{+} \rangle \langle \Phi_{00}^{+} \vert \\
    &= p \vert \Phi_{00}^{+} \rangle \langle \Phi_{00}^{+} \vert + \frac{(1-p)}{d} \sum_{n=0}^{d-1} \ket{nn}\bra{nn} \\
    &= \frac{1}{d} \sum_{n=0}^{d-1} \ket{nn}\bra{nn} + \frac{p}{d} \sum_{n \neq m} \ket{nn}\bra{mm}. 
\end{align*}  
By comparison of matrix elements, one can see that this can be rewritten as
\begin{align*}
     \mathcal{J}^{\textrm{ph}} = \alpha \ket{\Phi_{00}^+}\bra{\Phi_{00}^{+}} + \frac{(1-\alpha)}{d-1} \sum_{c=1}^{d-1} \ket{\Phi_{0c}^+}\bra{\Phi_{0c}^{+}}, \label{eq: choi-state dephase second}
\end{align*}
such that $\alpha = (p+1)/d$. To see this, consider  
\begin{align*}
      &\sum_{c=1}^{d-1} \ket{\Phi_{0c}^{+}}\bra{\Phi_{0c}^{+}} \\
      &= \sum_{c=1}^{d-1} \big( \mathbb{I} \otimes W_{0,c} \big) \ket{\Phi_{00}^+}\bra{\Phi_{00}^{+}} \big( \mathbb{I} \otimes W^\dagger_{0,c} \big) \\
      &= \sum_{c=1}^{d-1} \big( \mathbb{I}_A \otimes \sum_{n=1}^{d-1} \Omega^{cn} \ket{n}\bra{n} \big) \ket{\Phi_{00}^{+}}\bra{\Phi_{00}^{+}} \big( \mathbb{I} \otimes \sum_{m=0}^{d-1} \Omega^{-cm} \ket{m}\bra{m}  \big) \\
      &= \sum_{c=1}^{d-1} \sum_{n,m=0}^{d-1} \Omega^{c(n-m)} \big( \mathbb{I} \otimes \ket{n}\bra{n} \big) \ket{\Phi_{00}^{+}}\bra{\Phi_{00}^{+}} \big( \mathbb{I} \otimes \ket{m}\bra{m}  \big) \\
      &= d^{-1} \sum_{c=1}^{d-1} \sum_{n,m=0}^{d-1} \sum_{i,j=0}^{d-1} \Omega^{c(n-m)} \big( \mathbb{I} \otimes \ket{n}\bra{n} \big) \ket{ii}\bra{jj} \big( \mathbb{I} \otimes  \ket{m}\bra{m}  \big) \\
      &=d^{-1} \sum_{n,m=0}^{d-1} \bigg[ \sum_{c=1}^{d-1} \Omega^{c(n-m)} \bigg] \ket{nn}\bra{mm}.
\end{align*}
It can then be seen, using the sum of a geometric series, that 
\begin{equation}
    \sum_{c=1}^{d-1} \Omega^{c(n-m)} =
\begin{cases}
  -1 & ~\mathrm{if}~n \neq m \\
  (d-1) & ~\mathrm{if}~n=m 
\end{cases}
\end{equation}
Therefore, 
\begin{equation}
    \begin{split}
        \sum_{c=1}^{d-1} \ket{\Phi_{0c}^{+}}\bra{\Phi_{0c}^{+}} &= \frac{d-1}{d} \sum_{n=m}^{d-1} \ket{nn}\bra{nn} - \frac{1}{d} \sum_{n \neq m}\ket{nn}\bra{mm}.
    \end{split}
\end{equation}
Inputting this into the above gives 
\begin{equation}
    \begin{split}
        \mathcal{J}^{\textrm{ph}} &= \frac{\alpha}{d} \sum_{n,m=0}^{d-1} \ket{nn}\bra{mm} + \frac{1-\alpha}{d-1} \biggl[ \frac{d-1}{d} \sum_{n=m}^{d-1} \ket{nn}\bra{nn} - \frac{1}{d} \sum_{n \neq m}^{d-1}\ket{nn}\bra{mm} \biggl] \\
        &= \bigg[ \frac{\alpha}{d} + \frac{1-\alpha}{d} \bigg] \sum_{n=m}^{d-1} \ket{nn}\bra{nn} + \bigg[ \frac{\alpha}{d} - \frac{1-\alpha}{d(d-1)} \bigg] \sum_{n \neq m}^{d-1}\ket{nn}\bra{mm}_{AB} \\
        &= \frac{1}{d}  \sum_{n=m} \ket{nn}\bra{nn} + \frac{p}{d} \sum_{n \neq m}^{d-1}\ket{nn}\bra{mm},
    \end{split}
\end{equation}
if $\alpha=(p+1)/d$, the two equations are equivalent. 
:::

:::{tab-item} Depolarising Channel
:sync: tab5
**Qubits**

Let $ \rho \in \mathcal{H}^2$. The qubit depolarising channel acting on $ \rho $ is given by 

\begin{equation}
\mathcal{D}^{\textrm{pol}}_p(\rho) = p \rho + (1-p) \textrm{tr}\big[\rho\big] \mathbb{I}/2.
\end{equation} 

1. The *Kraus operators* are 
\begin{align*}
K_0 &= \sqrt{ \frac{1}{4} + \frac{3p}{4}} \mathbb{I}, ~ ~ K_1 = \sqrt{ \frac{1-p}{4}} X, \\
K_2 &= \sqrt{ \frac{1-p}{4}} Y, ~ ~ K_3 = \sqrt{ \frac{1-p}{4}} Z.
\end{align*}

2. The *Choi-state* is the so-called isotropic state,
\begin{equation}

\mathcal{J}^{\textrm{pol}} = p \ket{\Phi^+} \bra{\Phi^+}+ (1-p) \mathbb{I}/4,

\end{equation}

where $ \ket{\Phi^+} $ is the maximally entangled state, 
\begin{align*}

\ket{\Phi^{+}} &= \frac{\ket{0}\ket{0}+\ket{1} \ket{1}}{\sqrt{2}}, 
\end{align*}

**d-dimensional**

The depolarising channel acting on a $d$ dimensional Hilbert space, where $ \rho \in \mathcal{H}^d$, is 
\begin{equation}
\mathcal{D}^{\textrm{pol}}_p(\rho) = p \rho + (1-p)\mathbb{I}/d,
\end{equation} 
with 
\begin{equation}
\mathcal{J}^{\textrm{pol}} = p \ket{\Phi^+} \bra{\Phi^+}+ (1-p) \mathbb{I}/d^2.
\end{equation}

:::
::::