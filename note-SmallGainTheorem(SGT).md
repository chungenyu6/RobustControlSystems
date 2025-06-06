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
Related Note     : [[02-MIMORobustness]]


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

This section presents a first MIMO robust stability result moving beyond loop-at-a-time analysis. The result is presented for the general positive feedback system shown in Figure 4. This consists of an $n_y \times n_u$ LTI system $M$ and a complex matrix $\Delta \in \mathbb{C}^{n_u \times n_y}$. The system $M$ is assumed to be stable. A version of the small gain theorem, presented below, provides a necessary and sufficient condition for robust stability of this feedback connection.

![[Pasted image 20230427145857.png|300]]

Theorem 1. Assume $M$ is stable. The feedback system in Figure 4 is stable for all $\bar{\sigma}(\Delta)<m$ if and only if $\|M\|_{\infty} \leq \frac{1}{m}$.

Proof. Both directions of the proof rely a simple expression for the poles of the feedback system. Let $M$ have a state-space realization with matrices $(A, B, C, D)$. Assume, for simplicity, that $D=0$. In this case, the feedback system has the following state-space model:
$$
\begin{aligned}
\dot{x} & =(A+B \Delta C) x+B\left(r_2+\Delta r_1\right) \\
y & =C x
\end{aligned}
$$
The poles of this feedback system are given by the eigenvalues of $(A+B \Delta C)$. In particular, the feedback system has a pole on the imaginary axis at $\lambda=j \omega$ if and only if:
$$
\operatorname{det}(j \omega I-(A+B \Delta C))=0
$$
The system $M$ is stable and hence the eigenvalues of $A$ are all in the strict left half plane. Thus $\operatorname{det}(j \omega I-A) \neq 0$ and $(j \omega I-A)$ is invertible. It follows that the determinant in Equation 8 can be equivalently re-written as follows:
$$
\begin{aligned}
\operatorname{det}(j \omega I-(A+B \Delta C)) & =\operatorname{det}(j \omega I-A) \cdot \operatorname{det}\left(I-(j \omega I-A)^{-1} B \Delta C\right) \\
& =\operatorname{det}(j \omega I-A) \cdot \operatorname{det}\left(I-C(j \omega I-A)^{-1} B \Delta\right) \\
& =\operatorname{det}(j \omega I-A) \cdot \operatorname{det}(I-M(j \omega) \Delta)
\end{aligned}
$$
The second step follows because $\operatorname{det}\left(I+N_1 N_2\right)=\operatorname{det}\left(I+N_2 N_1\right)$ for any matrices $N_1$ and $N_2$ of compatible size. The last line follows from the definition of the transfer function for $M$. To summarize, the feedback system of $M$ and $\Delta$ has a pole on the imaginary axis at $\lambda=j \omega$ if and only if $I-M(j \omega) \Delta$ is singular.
$(\Leftarrow)$ Assume that $\|M\|_{\infty} \leq \frac{1}{m}$. This implies the following bound for all $\omega$ and for all $\bar{\sigma}(\Delta)<m$
$$
\|M(j \omega) \Delta\|_{2 \rightarrow 2} \leq\|M(j \omega)\|_{2 \rightarrow 2} \cdot\|\Delta\|_{2 \rightarrow 2}<1
$$
If $I-M(j \omega) \Delta$ is singular then there is a non-zero vector $w$ such that $w=M(j \omega) \Delta w$. This implies that $\|M(j \omega) \Delta\|_{2 \rightarrow 2} \geq 1$ contradicting the bound in Equation 9. Thus the bound in Equation 9 implies that $I-M(j \omega) \Delta$ is nonsingular for all $\omega$ and for all $\bar{\sigma}(\Delta)<m$. This further implies, by the arguments above, that the feedback system has no poles on the imaginary axis for all $\bar{\sigma}(\Delta)<m$.

This direction of the proof is completed by noting that the poles of the feedback system are continuous functions of $\Delta$. They are located at the eigenvalues of $A$ when $\Delta=0$. These eigenvalues are all in the strict left half of the complex plane because $M$ is stable. The poles migrate (move) in the complex plane as $\Delta$ is perturbed from zero. By continuity, the poles must cross the imaginary axis in order to migrate to the strict right half plane. As just shown, the feedback system has no poles on the imaginary axis for all $\bar{\sigma}(\Delta)<m$. Thus the poles remain in the strict left half plane, i.e. the feedback system is stable for all $\bar{\sigma}(\Delta)<m$.

$(\Rightarrow)$ This direction is shown by contradiction. Assume $\|M\|_{\infty}>\frac{1}{m}$. Hence there is some frequency $\omega_0$ such that $\bar{\sigma}\left(M\left(j \omega_0\right)\right)>\frac{1}{m}$. To shorten notation, denote $\bar{\sigma}\left(M\left(j \omega_0\right)\right)$ as $\bar{\sigma}$. By the SVD of $M\left(j \omega_0\right)$ there are vectors $w, z \in \mathbb{C}^{n_u}$ such that:
$$
\bar{\sigma} \cdot w=M\left(j \omega_0\right) z \text { and }\|w\|_2=\|z\|_2=1 .
$$
Select $\Delta_0:=\frac{1}{\bar{\sigma}} z w^*$ and note that:
$$
M\left(j \omega_0\right) \Delta_0 w=w \text { and } \bar{\sigma}\left(\Delta_0\right)<\frac{1}{m}
$$
Thus $I+M\left(j \omega_0\right) \Delta_0$ is singular. By the arguments above, the feedback system of $M$ and $\Delta_0$ has a pole on the imaginary axis at $\lambda=j \omega_0$. Hence the feedback system is unstable for a $\Delta_0$ with $\bar{\sigma}\left(\Delta_0\right)<\frac{1}{m}$.

The proof of this small gain theorem is constructive. In other words, if $\|M\|_{\infty}>\frac{1}{m}$ then the proof provides a procedure to construct a destabilizing perturbation with $\bar{\sigma}\left(\Delta_0\right)<\frac{1}{m}$.