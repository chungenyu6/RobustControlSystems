---
Note Status:
  - 🌱0
Note Type:
  - 📄note
Source Type:
  - 🏫lecture
tags:
  - control
  - linear_algebra
---
# Metadata
Source URL       : [UMN/EE5235: Robust Multivariable Control Systems]
Author              : [[Nicola Elia]]
Related Note     : [[02-MIMORobustness]], [[02-SystemNorms]]


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

The Euclidean norm of a vector $w \in \mathbb{C}^n$ measures the "size" or "length" of the vector. This is a specific instance of a more general class of $p$-norms defined by:
$$
\|w\|_p:=\left[\sum_{i=1}^n\left|w_i\right|^p\right]^{1 / p} \text { for } 1 \leq p<\infty
$$
The Euclidean norm corresponds to the case $p=2$ and hence it is also called the 2-norm. There are other norms that can be defined. In general, a vector norm is a function $\|\cdot\|: \mathbb{C}^n \rightarrow[0, \infty)$ satisfying the following axioms:
1. Positive Definiteness: $\|w\|=0$ if and only if $w=0_n$
2. Scalability: $\|\alpha w\|=|\alpha| \cdot\|w\|$ for any $w \in \mathbb{C}^n$ and $\alpha \in \mathbb{C}$.
3. Triangle Inequality: $\|w+z\| \leq\|w\|+\|z\|$ for any $w, z \in \mathbb{C}^n$.
It can be verified that all $p$-norms satisfy these axioms. These notes will use the Euclidean norm (2-norm) for complex vectors unless stated otherwise.

These same axioms can be used to define norms on the vector space of complex matrices. It will be most useful to consider a class of matrix norms based on the interpretation of $M \in \mathbb{C}^{n \times m}$ as a linear transformation mapping an input vector $w \in \mathbb{C}^m$ to an output vector $y:=M w \in \mathbb{C}^n$. Define the following function $\|\cdot\|_{2 \rightarrow 2}: \mathbb{C}^{n \times m} \rightarrow[0, \infty)$ :
$$
\|M\|_{2 \rightarrow 2}:=\max _{0 \neq w \in \mathbb{C}^m} \frac{\|M w\|_2}{\|u\|_2}
$$

This particular form is useful in some cases. Moreover, the induced 2-norm satisfies several additional properties including:
1. Submultiplicative property: If $A \in \mathbb{C}^{n \times m}$ and $B \in \mathbb{C}^{m \times l}$ then $\|A B\|_{2 \rightarrow 2} \leq\|A\|_{2 \rightarrow 2} \cdot\|B\|_{2 \rightarrow 2}$
2. Unitary Invariance: Let $M \in \mathbb{C}^{n \times m}$ be given. Then $\|M\|_{2 \rightarrow 2}=\left\|U^* M V\right\|_{2 \rightarrow 2}$ for any unitary matrices $U \in \mathbb{C}^{n \times n}$ and $V \in \mathbb{C}^{m \times m}$.
One critical fact is that the induced 2-norm for a matrix is equal to its maximum singular value. This result result is formally stated in the next theorem.
Theorem 2. $\|M\|_{2 \rightarrow 2}=\bar{\sigma}(M)$ for any $M \in \mathbb{C}^{n \times m}$
Proof. Let the SVD of $M$ be $M=U \Sigma V^*$. Recall from Equation 11 that $M v_1=\bar{\sigma}(M) u_1$ where $u_1$ and $v_1$ are the first columns of $U$ and $V$, respectively. Moreover, $\left\|u_1\right\|_2=\left\|v_1\right\|_2=1$ because $U$ and $V$ are unitary. Hence the gain achieved for the input vector $v_1$ is $\frac{\left\|M v_1\right\|_2}{\left\|v_1\right\|_2}=\bar{\sigma}(M)$. The induced 2-norm is the maximum gain over all (non-zero) input vectors. Hence it must be no less than the gain achieved with $v_1$, i.e. $\|M\|_{2 \rightarrow 2} \geq \bar{\sigma}(M)$.
Next apply the unitary invariance of the induced 2-norm:
$$
\|M\|_{2 \rightarrow 2}=\left\|U^* M V\right\|_{2 \rightarrow 2}=\|\Sigma\|_{2 \rightarrow 2}
$$
Apply the scaled form of the induced 2-norm (Equation 16) and the structure of $\Sigma$ to show:
$$
\|\Sigma\|_{2 \rightarrow 2}=\max _{w \in \mathbb{C}^m,\|w\|_2=1} \sqrt{\sum_{i=1}^k\left|\sigma_i(M) \cdot w_i\right|^2} \leq \max _{w \in \mathbb{C}^m,\|w\|_2=1} \bar{\sigma}(M) \cdot\|w\| \leq \bar{\sigma}(M)
$$
Thus, $\|M\|_{2 \rightarrow 2} \leq \bar{\sigma}(M)$. Combining this with the result $\|M\|_{2 \rightarrow 2} \geq \bar{\sigma}(M)$ from above yields $\|M\|_{2 \rightarrow 2}=\bar{\sigma}(M)$.

