---
title: Equivalence Relations 
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
abstract: An overview of partitions, equivalence relations and their relationship
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

We first consider partitions, before defining equivalence relations and detailing their relationship to partitions. 

## Partitions 
(equivalence_relation_page_partition_definition)=
A partition of a set $G$ is a collection of subsets $G_1,G_2, \ldots \subseteq G$ such that 
1. $G_i \neq \emptyset ~\forall~i$
    - No empty subsets 
2. $G_i \cap G_j = \emptyset$ if $i \neq j$
    - Disjointed subsets (no overlapping elements)
3. $\bigcup_i G_i = G$
    - The union of all subsets is the total set.

## Equivalence Relations

Let $G$ be a set. A relation $\sim$ on the set $G$ is an equivalence relation if it satisfies the following conditions
(Equivalence_Relations_page_definition_target)=
1. $g \sim g~\forall~g \in G$
    - Reflexivity 
2. $g \sim g' \iff g' \sim g$
    - Symmetry 
3. If $g \sim g'$ and $g \sim g''$ then $g \sim g''$
    - Transitivity 

For an element $g \in G$, its equivalence class is defined as
\begin{equation}
[g] \coloneqq \big\{ g' : g \sim g' \big\},
\end{equation} 
meaning the equivalence class is a subset of the total set, $[g] \subseteq G$.

## Equivalence Theorem 

The equivalence theorem states:

***Under any equivalence relation the corresponds equivalence classes will form a partition of the global set.*** 

***And, any partition of the global set will have a corresponding equivalence relation.***

Hence, equivalence relations and partitions are equivalent. 

:::{dropdown} Proof

Let $G$ be a set and $ \sim $ an equivalence relation such that 
\begin{equation}
[g] \coloneqq \big\{ g' : g \sim g' \big\}.
\end{equation} 

We will first prove the forward direction, and then the reverse.

***Forward***

Firstly, no equivalence class is empty as $g \in [g]$ due to the symmetry of the equivalence relation, i.e., $g \sim g$. 

Now we show that all equivalence classes are disjoint. 

Assume that $a \in [g]$ and $b \in [a]$. Then $g \sim a$ and $a \sim b$. Hence, due to transitivity $g \sim b$, meaning that $b \in [g]$. 

Therefore, anything in the equivalence class of $a$ is also in $[g]$, such that $[a] \subseteq [g]$. 

By symmetry, it can be seen that 
\begin{equation}
a \in [g] \iff  a \sim g \iff g \sim a \iff g \in [a].
\end{equation}

One can then run the above argument in reverse to show that $[g] \subseteq [a]$. Putting both statements together gives 
\begin{equation} 
[a] = [g].
\end{equation}
Hence, if the equivalence classes have any elements in common they are equal, meaning that the equivalence classes are equal or disjoint.   

Finally, as each element of $G$ is in at least one equivalence class, as $g \in [g]$, then the union of all equivalence classes is $G$. Hence, the equivalence classes form a [partition](#equivalence_relation_page_partition_definition) of $G$. 

***Reverse*** 

Consider a partition of $G$ given by 
\begin{equation}
P = \big\{ G_i : G_i \subseteq G \}.
\end{equation}

We now define an relation as 
\begin{equation}
a \sim b \iff a,b \in G_i
\end{equation}
for some $i$, meaning $a$ and $b$ are related if are elements of the same subset. The aim is then to show that this relation is a valid equivalence relation

Firstly, let $a=b \in G_i$. As each element of $G$ is in exactly one subset, $a \in G_i$ for some $i$ only. Hence, $a \sim a$ and the relation is reflexivity.

Now, suppose that $a \sim b$. It must therefore hold that $a,b \in G_i$ for some $i$ and not any other subset. Therefore, it must be the case that $b \sim a$, meaning that the relation is symmetric. 

Finally, let $a \sim b$ and $b \sim c$, meaning that $a,b \in G_i$ and $b,c \in G_j$ for some $i,j$. As the subsets are disjoint $G_i \cap G_j = \emptyset$ if and only if $i \neq j$. As there is overlap, it must therefore mean that $i=j$ and all elements belong to the same subset. Hence, it holds that $a \sim c$, meaning the relation is transitivity.

Therefore, the relation is a valid equivalence relation, meaning that for each partition a valid equivalence relation can be found. 

:::



