---
title: Quotient Groups 
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
abstract: The definition of quotient groups and an overview of why they are useful 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

## Quotient Groups

Let $(G, *)$ be a [group](#group-definition) and let $(H, *)$ be a [normal subgroup](#group_page_normal_subgroup_target) of $(G, *)$. 
(quotient_group_definition_target)=
The quotient group of $(G, *)$ with respect to $(H, *)$ is defined to be the group whose elements are all the left cosets of $H$: 
\begin{equation}
G/H \coloneqq \big\{ gH : g \in G \big\},
\end{equation}
with the binary operation being 
\begin{equation}
(g_1 H) \cdot (g_2 H) = (g_1 * g_2) H.
\end{equation}

As $(H, *)$ is normal, the left and right cosets are equal. Hence, the quotient group could also be defined via the right cosets. 

Moreover, normality of $(H, *)$ ensures that this binary operation is well defined. 
:::{dropdown} Proof

Let $a,b,c,d \in G$ such that $aH=cH$ and $bH=dH$ i.e., $c \in aH$ and $d \in bH$. 

The binary operation should be consistent if considered with respect to this alternative definition of the same coset. To see that this holds if $(H, *)$ is normal consider 
\begin{align*}
(a H) \cdot (b H) &= (a * b) H \\
&= a(bH) \\
&= a(dH) \\
&= a(Hd) \\
&= (aH)d \\
&= (cH)d \\
&= (cd)H.
\end{align*}.
:::  

### Purpose of Quotient Groups

The quotient group is a new group where $(H, *)$ is $e$ (the identity). Each of the elements of $G$ within each coset that makes up the elements of the quotient group can then be considered [equivalent](#Cosets_as_Equivalence_Classes_target) (under some equivalence relation). The quotient group can then be used to study the relationships between equivalent elements of $G$, rather then all elements of $G$. This is therefore an abstraction that could provide a simplification. 




