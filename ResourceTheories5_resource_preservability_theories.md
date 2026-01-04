---
title: Resource Preservability Theories
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
keywords: Static Resource Theories, Dynamical Resource Theory, Preservability
abstract: An overview of the framework of resource preservability theories
exports:
  - format: pdf
    template: physical_review_journals
    article_type: Report
--- 

The contents of this article is based on the work [](https://doi.org/10.22331/q-2020-03-19-244). 

Given some static resource theory $\mathcal{R}=(\mathfrak{O}, \mathfrak{F})$, a resource preservability theory aims to answers the following question:


_Given an allowed operation $\mathcal{E} \in \mathfrak{O}$, what is the ability of $\mathcal{E}$ to preserve the resource content of a system it acts upon?_

Resource preservability theories look to answer this question by formulating a [dynamical resource theory](#dynamical_resource_theory) within the allowed operations of the [static resource theory](#static_resource_theory). Resource preservability theories are therefore induced by some static resource theory, and treat the ability of an allowed operation of the static resource theories to preserve the (static) resource as a dynamical resource. 

## Framework

As with any resource theory, resource preservability theories have a set of allowed operations and free objects, which are a set of quantum supermaps [](10.1209/0295-5075/83/30004) (from quantum channels to quantum channels) and a set of quantum channels respectively. 

### Resource Annihilating Channels

In order to define these sets, we first need to define the notion of resource annihilating channels.
(Resource_Annihilating_channels_card_target)=
```{card} 
:header: **Resource Annihilating Channels**

The set of resource annihilating channels within a given static resource theory $\mathcal{R}=(\mathfrak{O}, \mathfrak{F})$ is
\begin{equation}
    \mathfrak{a} \coloneqq \big\{ \mathcal{E} \in \mathfrak{O} : \mathcal{E}(\rho) \in \mathfrak{F}~\forall~\rho \in \mathcal{D}(\mathcal{H}) \big\}.
\end{equation}

```

By definition, for all possible input states into a resource annihilating channel the output state will be a free state. Every channel $\mathfrak{O} \setminus \mathfrak{a}$ is then said to be able to _preserve_ the resource, as for all these channels there will exist at least one resourceful state that will retain some resource when output from the channel. Hence, the channel will have preserved some resource for at least that input state. 

Note, the term preserve can be justified as the channel is an allowed operation, meaning it cannot have generated any resource. Hence, all the resource within the output state must have also been in the input state.

### Free Objects 

The free objects — or free channels — of a resource preservability theory are those channels that cannot preserve any amount of resource i.e., the resource annihilating channels.
```{card} 
:header: **Free Channels of Resource Preservability Theories**

The free channels of a resource preservability theory, induced by some static resource theory, are the resource annihilating channels of the given static resource theory.

```

The allowed operations are built on the notion of super-channels, which are linear mappings of quantum channels to quantum channels. As with all allowed operations, they must be resource non-generating, meaning any channel output from an allowed operation of a resource preservability theory must not be able to preserve any more static-resource than the input channel. To achieve this, the pre-processing and post-processing channels used in the super-channel are allowed operations of the static resource theory. As these channels are static resource non-generating, they cannot enhance the resource preserving ability of the input channel. Moreover, to prevent the ancillary system in the definition of super-channels from being able to artificially provide preservability, a resource annihilating channel is included on this system. 


### Allowed Operations

The allowed operations of a resource preservability theory are defined as follows. 

```{card} 
:header: **Allowed Operations of Resource Preservability Theories**

The allowed operations of a resource preservability theory, induced by a static resource theory $\mathcal{R}=(\mathfrak{O}, \mathfrak{F})$, are mappings $\Pi: \mathfrak{P} \rightarrow \mathfrak{P}$, where $\mathfrak{P}$ is the set of quantum operations, of the form 
  \begin{equation}
      \Pi(\mathcal{E}) \coloneqq \Lambda_{b} \circ (\mathcal{E} \otimes \Lambda_{\mathrm{An}}) \circ \Lambda_a,
  \end{equation}
  where $\Lambda_X \in \mathfrak{O}~\forall~X \in \{a,b\}$ and $\Lambda_{\mathrm{An}} \in \mathfrak{a}$ ([Resource Annihilating Channels](#Resource_Annihilating_channels_card_target)). 

```

We note that $\Lambda_a$ and $\Lambda_b$ act on a larger system then $\Lambda_{\mathrm{An}}$. 

If the underlying static resource theory has super-activation, then $\Lambda_{\mathrm{An}}$ has a stricter requirement to be an absolutely resource annihilating channel [](https://doi.org/10.22331/q-2020-03-19-244). 

See [](#resource_preservability_theories) for schematic overview of resource preservability theories.

```{figure} resourceTheories5_resource_preservability_schematic
:label: resource_preservability_theories 
:alt: 
:align: 

A schematic overview of a resource preservability theory, showing that the resource preservability theory is built on top of a static resource theory. The allowed objects can be seen to be quantum channels, whilst the allowed operations are now super-channels.
```

## Example 

Here an example of a resource preservability theory, introduced in [](https://doi.org/10.48550/arXiv.2306.16848), is given. 

It is built upon the resource theory of informational non-equilibrium [](https://doi.org/10.1016/j.physrep.2015.04.003) and is therefore the resource theory of informational non-equilibrium preservability. 

Let the resource theory of informational non-equilibrium be given by $\mathcal{R} = (\mathfrak{F}^{\mathrm{st}}, \mathfrak{O}^{\mathrm{st}})$.

::::{tab-set}
:::{tab-item} Free Objects
:sync: tab1

The set of free channels in the resource theory of informational non-equilibrium preservability contains only the state preparation channel of the maximally mixed state
\begin{equation}
    \Lambda(\cdot) := \textnormal{tr}\big[\cdot\big]\Upsilon_{S}, ~ ~ \Upsilon_{S} \in \mathfrak{F}^{\mathrm{st}},
\end{equation}
as it is the channel that removes all resource of all possible input states.

:::
:::{tab-item} Allowed Operations
:sync: tab2

The allowed operations of the dynamical resource theory of informational non-equilibrium preservability have the following form 
(allowed_operations_resource_pres_target)=
\begin{equation}
      \Pi(\mathcal{N}) = \sum_{\kappa} p_{\kappa} \mathcal{E}_{\kappa} \circ \mathcal{N} \circ \mathcal{P}_{\kappa},
\end{equation}
where $\sum_{\kappa} p_{\kappa} = 1, p_\kappa \geq 0~\forall~\kappa$ and $\mathcal{E}_{\kappa}, \mathcal{P}_{\kappa} \in \mathfrak{O}^{\mathrm{st}} ~\forall~\kappa$. 

The allowed operations can also be formulated in terms of the Choi-state. 

:::{dropdown} Choi-state Formulation
Choi-Jamiołkowski isomorphism is a linear mapping between a quantum channel $\mathcal{N}$ and a bipartite quantum state $\mathcal{J}^\mathcal{N}$, given by 
\begin{equation}
    \mathcal{J}^\mathcal{N} = (\mathcal{I} \otimes \mathcal{N}) ( \vert \Phi^+ \rangle \langle \Phi^+ \vert ), 
\end{equation}
where $\ket{\Phi^+} := \frac{1}{\sqrt{d}} \sum_{i} \ket{ii}$. If there exists an allowed operation of the resource theory of informational non-equilibrium preservability, $\Pi$, such that $\mathcal{M} = \Pi(\mathcal{N})$, where $\mathcal{N}, \mathcal{M} \in \mathfrak{O}^\mathrm{st}$ then the Choi-state of $\mathcal{M}$ is given by 
\begin{equation}
    \begin{split}
        \mathcal{J}^\mathcal{M} &= \big( \mathcal{I} \otimes \sum_{\kappa} p_{\kappa} \mathcal{E}_{\kappa} \circ \mathcal{N} \circ \mathcal{P}_{\kappa} \big) \vert \Phi^+ \rangle \langle \Phi^+ \vert \\
        &= \sum_{\kappa} p_{\kappa} (\mathcal{I} \otimes \mathcal{E}_{\kappa})(\mathcal{I} \otimes \mathcal{N})(\mathcal{I} \otimes \mathcal{P}_{\kappa}) \vert \Phi^+ \rangle \langle \Phi^+ \vert \\
        &= \sum_{\kappa} p_{\kappa} (\mathcal{P}^{t}_{\kappa} \otimes \mathcal{I})(\mathcal{I} \otimes \mathcal{E}_{\kappa})(\mathcal{I} \otimes \mathcal{N}) \vert \Phi^+ \rangle \langle \Phi^+ \vert \\
        &= \sum_{\kappa} p_{\kappa} (\tilde{\mathcal{P}}_{\kappa} \otimes \mathcal{E}_{\kappa} )(\mathcal{J}^\mathcal{N}), 
    \end{split}
\end{equation}
where we define $\mathcal{P}^{t} \coloneqq \sum_{i} K_{i}^{t}(\cdot) \big(K_{i}^{\dagger}\big)^{t}$, which is the transpose of a channel $\mathcal{P}$ with Kraus representation $\mathcal{P} = \sum_{i} K_{i}(\cdot)K_{i}^{\dagger}$, where $(\cdot)^{t}$ is the transpose operation. In the penultimate line we have relabelled $\mathcal{P}^{t}_{\kappa} \rightarrow \tilde{\mathcal{P}}_{\kappa}$ given the transpose of a unital channel is still a unital channel. This gives the following Choi-state formulation of the allowed operations. 

```{card} 
:header: **Choi State Formalism of the Allowed Operations**

If there exists an allowed operation $\Pi \in \mathfrak{O}^\mathrm{dyn}$ between $\mathcal{M}, \mathcal{N} \in \mathfrak{O}^\mathrm{st}$, such that $\mathcal{M} = \Pi(\mathcal{N})$, then the corresponding Choi-states of the channels are related as 
\begin{equation}
    \begin{split}
        \mathcal{J}^\mathcal{M} &= \sum_{\kappa} p_{\kappa} (\mathcal{P}_{\kappa} \otimes \mathcal{E}_{\kappa} ) \big( \mathcal{J}^\mathcal{M} \big), 
    \end{split}
\end{equation}
where $\mathcal{E}_\kappa, \mathcal{P}_\kappa \in \mathfrak{O}^\mathrm{st} ~\forall~\kappa$. 

```
:::
::::
