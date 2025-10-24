---
title: Quantum Entropy Functions 
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
keywords: Entropy, Relative Entropy, Rényi Entropies. 
abstract: Some Quantum entropy functions and their properties are given. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---
(Entropy_Fucntions_target)=

## Von Neumann Entropy 

Let $\rho$ be a quantum state. The Von Neumann entropy of of $\rho$ is given by 
(Von_Neumann_Entropy_Equation_target)=
\begin{equation}
S(\rho) = -\textrm{tr}(\rho \log (\rho))
\end{equation}

It can be thought of as a measure of how far from a pure state a given state $\rho$ is.

:::{dropdown} Properties

1. $S(\rho) \geq 0$ where $S(\rho)=0$ iif $\rho$ is a pure state.
2. $ \max_{\rho} S(\rho)= \log{d}$ where $d$ is the dimension of the space. This occurs when $\rho$ is maximally mixed. 
3. $S(U \rho U^{\dagger}) = S(\rho)$ where $UU^{\dagger} = U^{\dagger}U = \mathbb{I}$. 
4. If $\sum_{i} p_i = 1$ then 
\begin{equation} 
S \bigg( \sum_{i} p_{i} \rho_i \bigg) \geq \sum_{i} p_{i} S(\rho_{i}).
\end{equation} 
5. $S(\rho \otimes \sigma) = S(\rho) \otimes S(\sigma)$.
6. $S(\rho_{AB}) \leq S(\rho_{A}) + S(\rho_{B})$, where $\rho_{A} = \textrm{tr}_{B}(\rho_{AB})$, etc.
7. $S(\rho_{AB}) \geq \vert S(\rho_{A}) - S(\rho_{B}) \vert$.
:::

## Quantum Relative Entropy 

Let $\rho, \sigma$ be quantum states. The quantum relative entropy is given by 
(quantum_relative_entropy)=
\begin{equation}
S( \rho \vert \vert \sigma) = \textrm{tr} \big( \rho \log(\rho) - \rho \log(\sigma)).
\end{equation}
if $\textrm{supp}(\rho) \subseteq \textrm{supp}(\sigma)$, it is defined as $+ \infty $ otherwise. 

It can be thought of as a measure of how similar two states $\rho$ and $\sigma$ are.

:::{dropdown} Properties

1. $S( \rho \vert \vert \sigma) \geq 0$ where $S( \rho \vert \vert \sigma) = 0$ iif $\rho = \sigma$
2. $S( \rho \vert \vert \sigma) \neq S( \sigma \vert \vert \rho)$
3. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
S( \rho \vert \vert \sigma) \geq S( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
4. $S( \rho \vert \vert \mathbb{I}/d) = \log(d) - S(\rho)$
5. If $\sum_{i} p_i = 1$ then 
\begin{equation}
S \bigg( \sum_{i} p_i \rho_i \vert \vert \sum_i p_i \sigma_i \bigg) \leq \sum_i p_i S(\rho_i \vert \vert \sigma_i) 
\end{equation}
:::

## Quantum $\alpha$-Rényi Entropies 

Let $\rho$ be a quantum state, the $\alpha$-Rényi entropy of $\rho$ is given by
\begin{equation}
S_{\alpha} = \frac{1}{1-\alpha} \log(\textrm{tr}(\rho^{\alpha})), ~ \alpha \in (0,1) \cap (1, \infty). 
\end{equation}
These are a set of functions that generalise entropy functions (such as the [Von Neumann Entropy](#Von_Neumann_Entropy_Equation_target)) by satisfying many of the same properties for all $\alpha$.  

In the limit of $\alpha \rightarrow 1$ the $\alpha$-Rényi entropy tends to the [Von Neumann Entropy](#Von_Neumann_Entropy_Equation_target),
\begin{equation}
S(\rho) = \lim_{\alpha \rightarrow 1} S_{\alpha}(\rho).
\end{equation}

:::{dropdown} Properties

1. $S_\alpha(\rho) \geq 0$ where $S_\alpha(\rho)=0$ iif $\rho$ is a pure state.
2. $ \max_{\rho} S_\alpha(\rho)= \log{d}$ where $d$ is the dimension of the space. This occurs when $\rho$ is maximally mixed. 
3. $S_\alpha(U \rho U^{\dagger}) = S_\alpha(\rho)$ where $UU^{\dagger} = U^{\dagger}U = \mathbb{I}$. 
4. If $\sum_{i} p_i = 1$ then 
\begin{align*} 
S_\alpha \bigg( \sum_{i} p_{i} \rho_i \bigg) \geq \sum_{i} p_{i} S_\alpha(\rho_{i}).
\end{align*} 
5. $S_\alpha(\rho \otimes \sigma) = S_\alpha(\rho) \otimes S_\alpha(\sigma)$.
6. $S_\alpha(\rho) - S_0(\rho_{B}) \leq S_\alpha(\rho_{AB}) \leq S_\alpha(\rho_{A}) + S_0(\rho_{B})$
7. $S_{\alpha_1}(\rho) \geq S_{\alpha_2}(\rho)$ for $1 < \alpha_1 \leq \alpha_2 $.
:::

## Quantum Relative $\alpha$-Rényi Entropies 

Let $\rho, \sigma$ be quantum states. The quantum relative $\alpha$-Rényi entropy is given by
\begin{equation}
S_{\alpha}(\rho \vert \vert \sigma) = \frac{1}{1-\alpha} \log \big[ \textrm{tr} \big( \rho^{\alpha} \sigma^{1-\alpha} \big) \big]
\end{equation}

The following entropy functions are limits of the quantum relative $\alpha$-Rényi entropies:

:::{dropdown} Properties

1. $S_{\alpha}(\rho \vert \vert \sigma) \geq 0$ with $S_{\alpha}(\rho \vert \vert \sigma)=0$ iif $\rho=\sigma$. 
2. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
S_{\alpha}(\rho \vert \vert \sigma) \geq S_{\alpha}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
:::

### Max Relative Entropy 

Let $\rho, \sigma$ be two operators such that $\rho \geq 0, ~\textrm{tr}(\rho)=1$ and $\sigma \geq 0$. The [max relative entropy](https://doi.org/10.1109/TIT.2009.2018325) is given by 
\begin{equation}
D_{\textrm{max}}(\rho \vert \vert \sigma) = \log \big[ \textrm{min} \{ \lambda~:~\rho \leq \lambda \sigma \} \big]
\end{equation}
or 
\begin{equation}
D_{\textrm{max}}(\rho \vert \vert \sigma) = \log \big[ \mu_{max} (\sigma^{\frac{1}{2}} \rho \sigma^{\frac{1}{2}} ) \big]
\end{equation}
where $\mu_{max}(A)$ is the maximum eigenvalue of the operator $A$ if $\textrm{supp}(\rho) \subseteq \textrm{supp}(\sigma)$, it is defined as $+ \infty $ otherwise.

:::{dropdown} Properties

1. $D_{\textrm{max}}( \rho \vert \vert \sigma) \geq 0$ with $D_{\textrm{max}}(\rho \vert \vert \sigma)=0$ if and only if $\rho=\sigma$ and both are states. 
2. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
D_{\textrm{max}}( \rho \vert \vert \sigma) \geq D_{\textrm{max}}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
3. If $\rho = \sum_{i}^{n} p_i \rho_i$ and $\sigma = \sum_i^{n} q_i \sigma_1$ are two mixtures, then 
\begin{equation}
D_{\textrm{max}}(\rho \vert \vert \sigma) \leq max_{i} D_{\textrm{max}}(\rho_i \vert \vert \sigma_i)
\end{equation}
4. $D_{\textrm{max}}(\rho \vert \vert \sigma) \geq S(\rho \vert \vert \sigma)$
5. $D_{\textrm{max}}(U \rho U^{\dagger} \vert \vert U \sigma U^{\dagger}) = D_{\textrm{max}}(\rho \vert \vert \sigma) $
6. $D_{\textrm{max}}(\rho \vert \vert \sigma) \leq - \log{\mu_{min}(\sigma)} $
7. $D_{\textrm{max}}(\rho_1 \otimes \rho_2 \vert \vert \sigma_1 \otimes \sigma_2) = D_{\textrm{max}}(\rho_1 \vert \vert \sigma_2) + D_{\textrm{max}}(\rho_2 \vert \vert \sigma_2)$   
8. $D_{\textrm{max}}(A:B) = D_{\textrm{max}}(\rho_{AB} \vert \vert \rho_A \otimes \rho_B)$
  - A mutual information like quantity 
:::

### Min Relative Entropy 

Let $\rho, \sigma$ be two operators such that $\rho \geq 0, ~\textrm{tr}(\rho)=1$ and $\sigma \geq 0$. The [min relative entropy](https://doi.org/10.1109/TIT.2009.2018325) is given by 
\begin{equation}
D_{\textrm{min}}(\rho \vert \vert \sigma) = - \log \big[ \textrm{Tr} \big( \Pi_{\rho} \sigma \big) \big]
\end{equation}
where $\Pi_{\rho}$ is the projector onto the support of $\rho$ if $\textrm{supp}(\rho) \subseteq \textrm{supp}(\sigma)$.

Note that
\begin{equation}
D_{\textrm{min}}( \rho \vert \vert \sigma) = \lim_{\alpha \rightarrow 0^+} S_{\alpha}(\rho \vert \vert \sigma)
\end{equation}

:::{dropdown} Properties

1. $D_{\textrm{min}}( \rho \vert \vert \sigma) \geq 0$ with $D_{\textrm{min}}(\rho \vert \vert \sigma)=0$ if $\rho=\sigma$ and both are states, or $\textrm{supp}(\rho)=\textrm{supp}(\sigma)$. In general, $D_{\textrm{min}}( \rho \vert \vert \sigma)=0$ if $\rho$ and $\sigma$ have identical supports. 
2. $D_{\textrm{min}}( \rho \vert \vert \sigma) \leq D_{\textrm{max}}( \rho \vert \vert \sigma)$
3. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
D_{\textrm{min}}( \rho \vert \vert \sigma) \geq D_{\textrm{min}}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
4. If $\rho = \sum_{i}^{n} p_i \rho_i$ and $\sigma = \sum_i^{n} p_i \sigma_1$ are two mixtures, then 
\begin{equation}
D_{\textrm{min}}(\rho \vert \vert \sigma) \leq \sum_i p_i D_{\textrm{min}}(\rho_i \vert \vert \sigma_i)
\end{equation}
5. $D_{\textrm{min}}(\rho \vert \vert \sigma) \leq S(\rho \vert \vert \sigma)$
6. $D_{\textrm{min}}(U \rho U^{\dagger} \vert \vert U \sigma U^{\dagger}) = D_{\textrm{min}}(\rho \vert \vert \sigma) $
7. $D_{\textrm{min}}(\rho \vert \vert \sigma) \leq - \log{\mu_{min}(\sigma)} $
8. $D_{\textrm{min}}(A:B) = D_{\textrm{min}}(\rho_{AB} \vert \vert \rho_A \otimes \rho_B)$
  - A mutual information like quantity 
:::

## Quantum Sandwiched $\alpha$-Rényi Entropies

Let $\rho, \sigma$ be quantum states. The quantum quantum sandwiched $\alpha$-Rényi entropy is given by 
\begin{equation}
D_{\alpha}( \rho \vert \vert \sigma) = \frac{1}{1-\alpha} \log { \bigg[ \textrm{tr} \big( \sigma^{\frac{1-\alpha}{2 \alpha}} \rho \sigma^{\frac{1-\alpha}{2 \alpha}} \big)^{\alpha} \bigg] } .
\end{equation}
if $\textrm{supp}(\rho) \subseteq \textrm{supp}(\sigma)$, it is defined as $+ \infty $ otherwise.

:::{dropdown} Properties

1. $D_\alpha(\rho \vert \vert \sigma) \geq 0$ where $D_\alpha(\rho \vert \vert \sigma)$ iif $\rho=\sigma$.
2. If $\mathcal{E}$ is a quantum channel and $\alpha \in [\frac{1}{2}, 1)$ and $(1, \infty)$ then 
\begin{equation}
D_{\alpha}( \rho \vert \vert \sigma) \geq D_{\alpha}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://doi.org/10.1063/1.4838855)
3. $D_{\alpha}(\rho \vert \vert \sigma) \geq D_{\beta}(\rho \vert \vert \sigma)$ if $\alpha \geq \beta$. 
:::

The following entropy functions are limits of the quantum sandwiched $\alpha$-Rényi entropies:

### Min Relative Entropy 

Let $\rho, \sigma$ be two states, the min relative entropy is given by 
\begin{equation}
D_{\textrm{min}}(\rho \vert \vert \sigma) = - \log \big[ \textrm{Tr} \big( \sqrt{\rho} \sqrt{\sigma} \big)^{2} \big]
\end{equation}

:::{dropdown} Properties

1. $D_{\textrm{min}}( \rho \vert \vert \sigma) \geq 0$ with $D_{\textrm{min}}(\rho \vert \vert \sigma)=0$ iif $\rho=\sigma$. 
2. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
D_{\textrm{min}}( \rho \vert \vert \sigma) \geq D_{\textrm{min}}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
:::

## Hypothesis Testing Relative Entropy

Let $\rho, \sigma$ be two states, the hypothesis testing relative entropy
\begin{equation}
D_{H}^{\epsilon}(\rho \vert \vert \sigma) \coloneqq - \log  \inf_{ \substack{0 \leq Q \leq \mathbb{I}, \\ \textrm{tr}[ Q \rho ]  \geq 1 - \epsilon}} \textrm{tr}\big[Q \sigma \big]
\end{equation}

:::{dropdown} Properties

1. $D_{H}^{\epsilon}(\rho \vert \vert \sigma) \geq 0$, where $D_{H}^{\epsilon}(\rho \vert \vert \sigma) = 0$ iif $\rho = \sigma$.
2. If $\mathcal{E}$ is a quantum channel then 
\begin{equation}
D_{H}^{\epsilon}(\rho \vert \vert \sigma) \geq D_{H}^{\epsilon}( \mathcal{E}(\rho) \vert \vert \mathcal{E}(\sigma)).
\end{equation}
  - This is the [data processing inequality.](https://en.wikipedia.org/wiki/Data_processing_inequality)
3. Let $H_b(\cdot)$ be the [binary entropy function](https://en.wikipedia.org/wiki/Binary_entropy_function) then 
\begin{equation}
 D_{H}^{\epsilon}(\rho \vert \vert \sigma) \leq \frac{ \bigg( S(\rho \vert \vert \sigma ) + H_b(\epsilon) \bigg)}{1 - \epsilon}.
 \end{equation}
4. For any $ \epsilon \in (0,1)$ in 
\begin{equation}
\lim_{n \rightarrow \infty} \frac{1}{n} D_{H}^{\epsilon}(\rho^{\otimes n} \vert \vert \sigma^{\otimes n}) = S(\rho \vert \vert \sigma).
\end{equation}
  - This is the Quantum Stein's Lemma
:::