---
Note Status:
  - 🌱0
Note Type:
  - 📄note
Source Type:
  - 🏫lecture
tags:
  - control
---
# Metadata
Source URL       : [UMN/EE5235: Robust Multivariable Control Systems]
Author              : [[Nicola Elia]]
Related Note     : [[02-RobustStability]]


---

# Permanent Note (Evergreen)
	5th review: 1 sentence to conclude the idea
## Overview
	1 idea 1 note only


## Insight
### - Pros & Cons


### - Future


---

# Literature Note (Summary)
	4th review: summerize in your own words
	* 4 Questions to Ask Yourself
	  1.  How does the idea relate to me?
	  2.  Does this fact can be explained by other things?
	  3.  How X effects Y?
	  4.  How can I explain Z by utilizing this idea?


---

# Fleeting Note 
	1st - 3rd review: orginal -> underline -> highlight

## Definition
Lemma 2 is the key technical result that must be generalized in order to compute robust stability margins with structured uncertainty. This is a purely linear algebra result stated for a given $M \in \mathbb{C}^{n_v \times n_w}$. A consequence of this lemma is that $\operatorname{det}(I-M \Delta) \neq 0$ for any $\Delta \in \mathbb{C}^{n_w \times n_v}$ with $\bar{\sigma}(\Delta)<\frac{1}{\bar{\sigma}(M)}$. Moreover, the proof constructs a perturbation $\Delta_0$ with $\operatorname{det}\left(I-M \Delta_0\right)=0$ and $\bar{\sigma}\left(\Delta_0\right)=\frac{1}{\bar{\sigma}(M)}$. It follows that $\Delta_0$ is a smallest perturbation causing singularity of $I-M \Delta$. This leads to the following optimization interpretation:
$$
\begin{aligned}
\frac{1}{\bar{\sigma}(M)}= & \min _{\Delta \in \mathbb{C}^{n_w \times n_v}} \bar{\sigma}(\Delta) \\
& \text { subject to: } \operatorname{det}(I-M \Delta)=0
\end{aligned}
$$
Thus the maximum singular value is inversely related to the minimum norm (unstructured) matrix $\Delta \in \mathbb{C}^{n_w \times n_v}$ causing singularity of $I-M \Delta$. This discussion motivates the following definition for the structured singular value.

Definition 1. Let $\Delta \subseteq \mathbb{C}^{n_w \times n_v}$ denote a structured set of complex uncertainty. For $M \in$ $\mathbb{C}^{n_v \times n_w}$ define the structured singular value $\mu_{\Delta}(M)$ as:
$$
\mu_{\Delta}(M):=\left[\min _{\Delta \in \Delta} \bar{\sigma}(\Delta) \text { s.t. } \operatorname{det}(I-M \Delta)=0\right]^{-1}
$$
If no $\Delta \in \Delta$ causes $\operatorname{det}(I-M \Delta)=0$ then $\mu_{\Delta}(M):=0$.
This is a purely linear algebra definition, i.e. $M$ is a matrix and $\boldsymbol{\Delta}$ contains only real or complex uncertainty but no dynamic uncertainty. The structured singular value can be computed exactly for certain uncertainty structures. For example, unstructured complex uncertainty corresponds to $\boldsymbol{\Delta}=\mathbb{C}^{n_w \times n_v}$. For this case, $\mu_{\Delta}(M)=\bar{\sigma}(M)$ based on the optimization result for the maximum singular value (Equation 8). However, computing $\mu_{\Delta}$ is known to be a computationally difficult problem for general uncertainty structures. It is equivalent to other known difficult problems in theoretical computer science, e.g. the traveling salesman problem. This essentially rules out "exact" methods to compute the structured singular value. Instead, the aim is to develop reliable algorithms which quickly yield decent lower and upper bounds on $\mu_{\Delta}$. These are briefly discussed in the next two subsections.

Finally, the definition of $\mu_{\Delta}$ leads to the following generalization of Lemma 2. optimization
Lemma 5. Let $M \in \mathbb{C}^{n_v \times n_w}$ and $\Delta \subseteq \mathbb{C}^{n_w \times n_v}$ be given. Then $\operatorname{det}(I-M \Delta) \neq 0$ for all $\Delta \in \boldsymbol{\Delta}$ with $\bar{\sigma}(\Delta)<m$ if and only if $\mu_{\Delta}(M) \leq \frac{1}{m}$.

Proof. This lemma follows almost immediately from the definition of $\mu_{\Delta}$. If no $\Delta \in \Delta$ causes $\operatorname{det}(I-M \Delta)=0$ then the lemma is trivially true. Hence assume there is at least one $\Delta \in \boldsymbol{\Delta}$ such that $\operatorname{det}(I-M \Delta)=0$.
$(\Leftarrow)$ Assume $\mu_{\Delta}(M) \leq \frac{1}{m}$. By definition, the smallest $\Delta \in \Delta$ such that $\operatorname{det}(I-M \Delta)=0$ has $\bar{\sigma}(\Delta) \geq m$. In other words, $\operatorname{det}(I-M \Delta) \neq 0$ for all $\Delta \in \Delta$ with $\bar{\sigma}(\Delta)<m$.
$(\Rightarrow)$ This direction is shown by contradiction. Assume $\mu_{\Delta}(M)>\frac{1}{m}$. Again, by definition, the smallest $\Delta \in \Delta$ such that $\operatorname{det}(I-M \Delta)=0$ has $\bar{\sigma}(\Delta)<m$. In other words, there is a $\Delta_0 \in \Delta$ with $\bar{\sigma}\left(\Delta_0\right)<m$. such that $\operatorname{det}\left(I-M \Delta_0\right)=0$.

---
${ }^{\ddagger}$ If $\Delta$ consists of only real parameter uncertainty then it is possible to have $\operatorname{det}(I-M \Delta) \neq 0$ for all $\Delta \in \Delta$. As a simple example, let $\Delta:=\mathbb{R}$ corresponding to a single real perturbation. If $M=5+2 j$ then $1-M \delta \neq 0$ for all $\delta \in \boldsymbol{\Delta}$.

---
## Upper Bounds on $\mu_{\Delta}$
Suppose two uncertainty sets are given with $\boldsymbol{\Delta}_1 \subset \boldsymbol{\Delta}_2$. The minimization in the definition of $\mu_{\boldsymbol{\Delta}_2}$ is over a larger set of matrices than for $\mu_{\boldsymbol{\Delta}_1}$. Minimizing over the larger set $\boldsymbol{\Delta}_2$ can only decrease the cost leading to a larger structured singular value, i.e. $\mu_{\boldsymbol{\Delta}_2} \geq \mu_{\boldsymbol{\Delta}_1}$. As a concrete example, every perturbation in $\boldsymbol{\Delta}_1:=\left\{\left[\begin{array}{cc}\delta & 0 \\ 0 & \Delta\end{array}\right]: \delta \in \mathbb{R}, \Delta \in \mathbb{C}^{2 \times 3}\right\}$ is also in $\boldsymbol{\Delta}_2:=\mathbb{C}^{3 \times 4}$. Hence $\mu_{\boldsymbol{\Delta}_1}(M) \leq \mu_{\boldsymbol{\Delta}_2}(M)=\bar{\sigma}(M)$

In fact, any uncertainty structure satisfies $\Delta \subseteq \mathbb{C}^{n_w \times n_v}$. Thus the structured singular value is bounded by $\mu_{\Delta_1}(M) \leq \bar{\sigma}(M)$. This fact forms the basis for upper bounds on the structured singular value. Tighter upper bounds are computed using scalings that account for the non-uniqueness in the LFT representation.


## Lower Bounds on $\mu_{\Delta}$
Let $\left\{\lambda_i(M)\right\}_{i=1}^n$ denote the eigenvalues of a matrix $M \in \mathbb{C}^{n \times n}$. Define the spectral radius of $M$ as $\rho(M):=\max _i\left|\lambda_i(M)\right|$. If $\boldsymbol{\Delta}:=\{\delta I: \delta \in \mathbb{C}\}$ then $\mu_{\Delta}(M):=\rho(M)$. A simple power iteration can be used to compute $\rho(M)$. An outline of this power iteration is given in the attached notes. This power iteration can be generalized to develop a power iteration to compute lower bounds on $\mu_{\Delta}(M):=\rho(M)$ for more complicated uncertainty structures.