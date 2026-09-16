---
title: Maps 
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
keywords: Groups, Group Theory. 
abstract: Maps between groups and their properties 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

## Maps Between Groups

Let $(G, *)$ and $(H, \cdot)$ be [groups](#group_page_group_definition). 

A map $f$ between these groups is a function that maps an element from $(G, *)$ to an element of $(H, \cdot)$:
\begin{equation}
f : G \rightarrow H. 
\end{equation}

## Homomorphism 

A map $f : G \rightarrow H$ is said to be a homomorphism if for all $g_1, g_2 \in G$ it holds that 
\begin{equation}
f(g_1 * g_2) = f(g_1) \cdot f(g_2).
\end{equation}
From this definition, it can be seen that the identity element of $(G, *)$, denoted $e_G \in G$, is mapped to the identity element of $(H, \cdot)$, denoted $e_H \in H$, i.e.,  
\begin{equation}
f(e_G) = e_H.
\end{equation}
:::{dropdown} Proof

Let $g_1 = a$ and $g_2 = e_G$. Then 
\begin{align*}
f(g_1 * e_G) &= f(g_1) \\
&= f(g_1) \cdot f(e_G) 
\end{align*}
As the identity is the unique element of the group that maps group elements to themselves it must hold that 
\begin{equation}
e_H = f(e_G).
\end{equation}
:::
Using this condition, it can then be seen that inverses are mapped to inverses 
\begin{equation}
f(g^{-1}) = f(g)^{-1}.
\end{equation}
:::{dropdown} Proof

Let $g_1 = g^{-1}$ and $g_2 = g$. Then 
\begin{align*}
f(g * g^{-1}) &= f(e_G) \\
&= f(g) \cdot f(g^{-1}). 
\end{align*}
From above $f(e_G) = e_H$, meaning that
\begin{equation}
f(g) \cdot f(g^{-1}) = e_H.
\end{equation}
As the inverse is unique by [definition](#group_page_group_definition), it holds that  
\begin{equation}
f(g^{-1}) = f(g)^{-1}.
\end{equation}
:::

Maps that are homomorphism are therefore said to preserve the group structure. 

### Monomorphism

A group homomorphism that is [injective](#injective_linear_maps_target), meaning that each distinct input element is mapped to a different output element. 

### Epimorphism 

A group homomorphism that is [surjective](#Surjective_linear_maps_target), meaning that every point in the codomain (output space) can be reached via some input element. 

### Isomorphism 
(Isomorphism_definition_target_group_definitions)=
A group homomorphism that is [bijective](#bijective_definition_target), meaning that it is both injective and surjective.

Given groups $(G, *)$ and $(H, \cdot)$, if an isomorphism exists between the groups, they are said to be isomorphic. 

#### Properties 

- The [kernel](#kernel_definition_maps_page) of an isomorphism from a group $(G, *)$ to $(H, \cdot)$ always contains only the idenity of $G$,
\begin{equation}
{\rm Ker}(f) = \big\{e_G \big\}.
\end{equation}

- Isomorphic groups are said to be equivalent in terms of their group structure, as they differ only in the label of each element. 

- The inverse of an isomorphism is also an isomorphism.

- If $(G, *)$ and $(H, \cdot)$ are isomorphic, then $(G, *)$ is [abelian](#albelian_group_definition) if and only if $(H, \cdot)$ is [abelian](#albelian_group_definition).  

## Kernel

Let $f : G \rightarrow H$ be a homomorphism between $(G, *)$ and $(H, \cdot)$. The kernel of $f$ is given by 
(kernel_definition_maps_page)=
\begin{equation}
{\rm Ker}(f) = \big\{ g \in G : f(g) = e_H \big\}.
\end{equation}
The kernel of a homomorphism is therefore the set of elements in $G$ mapped to the identity element in $H$. 

The kernel is a [normal subgroup](#group_page_normal_subgroup_target) of $(G, *)$.

:::{dropdown} Proof

To be normal the kernel should be closed under conjugation by any element $g \in G$. 

To see that this holds, let $\tilde{g} \in {\rm Ker}(f)$. Now consider the map of this element under conjugation by $g$, 
\begin{align*}
f(g * \tilde{g} * g^{-1}) &= f(g) \cdot f(\tilde{g}) \cdot f(g^{-1}) \\
&= f(g) \cdot e_H \cdot f(g^{-1}) ~ ~ ~ {\rm as} ~ ~f(\tilde{g}) = e_H \\
&= f(g) \cdot f(g^{-1}) \\
&= e_H.
\end{align*}
Therefore, $\forall ~g \in G$ it holds that if $\tilde{g} \in {\rm Ker}(f)$ then $g \tilde{g} g^{-1} \in {\rm Ker}(f)$, meaning that ${\rm Ker}(f)$ is normal.
:::