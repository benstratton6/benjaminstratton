---
title: Cosets
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
abstract: Cosets of discrete groups and normal groups. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

Here we define cosets and give some of their properties. We then define normal subgroups. 

## Definition

Let $(G, *)$ be a group and let $(H, *)$ be a [subgroup](#group_page_subgroup_definition) of $(G, *)$. 

For an element $g \in G$:
(group_theory_page_cosets_definition)=
- The left coset of $(H, *)$ containing $g$ is $gH = \big\{ g*h : h \in H \big\}$
- The right coset of $(H, *)$ containing $g$ is $Hg = \big\{ h*g : h \in H \big\}$

Cosets shift a subgroup within the global group by some group element $g \in G$.

### Coset Properties

- If the group $(G, *)$ is abelian, then the left and right coset are the same. 

- Two cosets are either the same, or they are disjointed (they do not overlap at all). Formally, let $a,b \in G$, then 
\begin{equation}
aH \cap bH \neq \emptyset ~ ~ &\implies aH = bH \\
aH \neq bH ~ ~ &\implies aH \cap bh \neq \emptyset \\
\end{equation}
:::{dropdown} Proof

Let $(G, *)$ be a [group](#group_page_group_definition) and let $(H, *)$ be a [subgroup](#group_page_subgroup_definition) of $(G, *)$. Then, let 
\begin{align*}
aH &\coloneqq  \big\{ a * h : h \in H \big\} \\
bH &\coloneqq \big\{ b * h : h \in H \big\}
\end{align*}
Now, assume that there exists an $x \in G$ such $x \in aH$ and $x \in bH$, meaning that the cosets intersect. 

By definition, there therefore exists a $h_1, h_2 \in H$ such that $x = a*h_1$ and $x = b*h_2$. 

Using the properties of a group, it therefore holds that $b^{-1}*a = h_1^{-1}*h_2$.

As $(H, *)$ is a group, it therefore also holds that $h_1^{-1}*h_2 = b^{-1}*a \in H$. 

One can therefore write $a = b*(b^{-1}*a)$, and see that $a$ is equal to $b$ up to some element $h \in H$, meaning that $a \in bH$. 

One can therefore concluded that $aH \subseteq bH$. Running the argument in reverse, one gets that $bH \subseteq aH$, such that $aH=bH$. The same argument works for the right cosets, which completes the proof. 
:::

- Due to the above, each element of $G$ is in exactly one coset.

- $(H, *)$ is a coset of $(G, *)$ where the considered element is the identity $e \in G$, i.e., $eH=H$. This is the only coset that is a subgroup, as it is the only coset containing $e$. 

- Each coset is equal in size.
:::{dropdown} Proof

Assume that $H$ has $n$ elements 
\begin{equation}
H = \big\{ h_1, h_2, \ldots, h_n \big\}.
\end{equation}

There are then $n$ elements of $gH$, 
\begin{equation}
gH = \big\{ g*h_1, g*h_2, \ldots, g*h_n \big\}.
\end{equation}

Now, assume that there exists an $i,j \in [1,n]$ such that 
\begin{equation}
g * h_i = g * h_j.
\end{equation}
Using the inverse of $g$, this implies that $h_i = h_j$. 

Therefore, $gH$ can have no duplicates and must contain $n$ different elements. 

This was independent of the choice of $g$, meaning that for all $g \in G$ the size of the produced cosets with be equal to the size of the subset $H$. 

:::


Cosets therefore split $G$ into equal sized, disjointed subsets. 
(Cosets_as_Equivalence_Classes_target)=
### Cosets as Equivalence Classes

Let $(G, *)$ be a group and let $(H, *)$ be a [subgroup](#group_page_subgroup_definition) of $(G, *)$. 

Now, define an [equivalence relation](#Equivalence_Relations_page_definition_target) as $g \sim g'$ if $g^{-1}*g' \in H$ i.e., the binary operation of the inverse of $g$ and $g'$ is in $H \subseteq G$. 

The corresponding equivalence classes for this equivalence relation are 
\begin{equation}
[g] = \big\{ a \in G : g^{-1}*a \in H \big\}.
\end{equation}

Now, if $x \in [g]$, then there exists a $h \in H$ such that $g^{-1}*x=h$. 

Therefore, $x=g*h$, meaning that the equivalence classes can also be written as 
\begin{equation}
[g] = \big\{ g*h : h \in H \big\} = gH,
\end{equation}
meaning that the equivalence classes relating to this equivalence relation are exactly the left cosets of the group $(G, *)$ with respect to the subgroup $(H, *)$. 

The cosets can therefore always be seen to be equivalence classes of the group under some equivalence relation. 

Moreover, as equivalence relations always partition the set, this is an alternative proof that cosets are disjointed.   

## Normal Subgroups
(group_page_normal_subgroup_target)=
A [subgroup](#group_page_subgroup_definition) $(N, *)$ of $(G, *)$ is called normal if $\forall g \in G$ it holds that
\begin{equation}
gN = Ng,
\end{equation}
meaning that the left and right [cosets](#group_theory_page_cosets_definition) are equal. 

This is true if $\forall g \in G$ it holds that $g N g^{-1} =  N$, meaning that 
\begin{equation}
\big\{ g * n_i * g^{-1} : n_i \in N \big\} = N,
\end{equation} 
such that taking every element of the set $N$ and conjugating it by $g$ gives back the full set $N$. Note, this is a weaker notion then all elements commuting. 




