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
Related Note     : [[02-HinfOptmlCtrl]]


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

This section provides a solution to the $H_{\infty}$ state-feedback problem. Consider the linear timeinvariant system $G$ :
$$
\begin{aligned}
\dot{x}(t) & =A x(t)+B_1 d(t)+B_2 u(t) \\
e(t) & =C_1 x(t) \quad+D_{12} u(t) \\
y(t) & =x(t)
\end{aligned}
$$
Let $\gamma>0$ be given. The goal is to design a (constant) state feedback gain $K \in \mathbb{R}^{n_u \times n_x}$ such that $u=K x$ stabilizes $F_L(G, K)$ and achieves $\left\|F_L(G, K)\right\|_{\infty}<\gamma$ or determine that no such gain exists. Assume $G$ satisfies the following assumptions:
1. $\left(A, B_2\right)$ is stabilizable: This ensures that there is a gain $K$ that stabilizes the plant $G$.
2. $\left(A, C_1\right)$ is detectable: This ensures that unstable modes appear in the output error.
3. $D_{11}=0, D_{12}^T C_1=0_{n_u \times n_x}$, and $D_{12}^T D_{12}=I_{n_u}$ : These assumptions on the feedthrough matrix simplify the derivation. These assumptions can be relaxed.
Let $u=K x$ be a given state feedback. The dynamics for the closed-loop $F_L(G, K)$ are:
$$
\begin{aligned}
\dot{x}(t) & =\left(A+B_2 K\right) x(t)+B_1 d(t) \\
e(t) & =\left(C_1+D_{12} K\right) x(t)
\end{aligned}
$$
By the bounded real lemma, the gain $K$ stabilizes $F_L(G, K)$ and achieves $\left\|F_L(G, K)\right\|_{\infty}<\gamma$ if and only if there exists $X \geq 0$ such that $A+\mathrm{B}_2 \mathrm{~K}+\gamma^{-2} B_1 B_1^P$ is Hurwitz and satisfies:
$$
\left(A+B_2 K\right)^T X+X\left(A+B_2 K\right)+\left(C_1+D_{12} K\right)^T\left(C_1+D_{12} K\right)+\gamma^{-2} X B_1 B_1^T X=0
$$
Thus $H_{\infty}$ state-feedback design corresponds to finding the gain $K$ and the matrix $X$ that proves stability and performance. Equation 4 is an algebraic Riccati equation in $X$ for any given $K$. However, the simultaneous search for both $K$ and $X$ is more difficult. The next theorem demonstrates that this can be transformed in an equivalent, but different, Riccati condition with no dependence on the gain $K$.

Theorem 1. Consider the linear time-invariant system $G$ given in Equation 2 and satisfying assumptions 1-3 above. Let $\gamma>0$ be given. The following statements are equivalent:
1. There exists a feedback gain $K$ such that $F_L(G, K)$ is stable $\left(A+B_2 K\right.$ is Hurwitz) and $\left\|F_L(G, K)\right\|_{\infty}<\gamma$
2. There exists a unique $X \geq 0$ such that $A+\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) X$ is Hurwitz and satisfying the ARE:
$$
A^T X+X A+C_1^T C_1+X\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) X=0
$$
3. There exists $Y>0$ satisfying the strict ARI:
$$
A^T Y+Y A+C_1^T C_1+Y\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) Y<0
$$
Proof.
$(\mathbf{2} \Rightarrow \mathbf{1})$ : Define $K:=-B_2^T X$ and re-write the ARE in Equation 5 as:
$$
\begin{aligned}
0 & =A^T X+X A+C_1^T C_1+\gamma^{-2} X B_1 B_1^T X+\underbrace{\left(K^T K+K^T B_2^T X+X B_2 K\right)}_{=-X B_2 B_2^T X} \\
& =\left(A+B_2 K\right)^T X+X\left(A+B_2 K\right)+\left(C_1+D_{12} K\right)^T\left(C_1+D_{12} K\right)
\end{aligned}
$$
The second equality uses $C_1^T D_{12}=0$ and $D_{12}^T D_{12}=I$. Moreover, note that $X \geq 0$ and $\left(A+B_2 K\right)+\gamma^{-2} B_1 B_1^T$ is Hurwitz by assumption. It follows from the Bounded Real Lemma that $A+B_2 K$ is Hurwitz and $\left\|F_L(G, K)\right\|_{\infty}<\gamma$
$(\mathbf{1} \Rightarrow \mathbf{3})$ : By the Bounded Real Lemma, there exists $Y>0$ such that
$$
\left(A+B_2 K\right)^T Y+Y\left(A+B_2 K\right)+\underbrace{\left.C_1+D_{12} K\right)^T\left(C_1+D_{12} K\right)}_{=C_1^T C_1+K^T K}+\gamma^{-2} Y B_1 B_1^T Y<0
$$
The equality in the underbrace again uses $C_1^T D_{12}=0$ and $D_{12}^T D_{12}=I$. Next, complete the square to rewrite this matrix inequality in the following form:
$$
A^T Y+Y A+C_1^T C_1+Y\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) Y+\underbrace{\left(K+B_2^T Y\right)^T\left(K+B_2^T Y\right)}_{\geq 0}<0
$$
The last term is positive semidefinite and hence the remaining terms must be negative definite, i.e. $Y>0$ satisfies Equation 6 .
$(3 \Rightarrow 2)$ : The part of the proof is technical but involves the connections between the solutions of Riccati equations and the corresponding inequality.

The ARE condition combined with bisection can be used to solve the state-feedback problem within any desired tolerance. First, compute any stabilizing state feedback gain $K_1$, e.g. by by pole-placement. Define the lower and upper bounds $\underline{\gamma}:=0$ and $\bar{\gamma}:=\left\|F_L\left(G, K_1\right)\right\|_{\infty}$. The optimal cost for the state feedback problem thus satisfies $\gamma^* \in[\underline{\gamma}, \bar{\gamma}]$. Select $\gamma:=\frac{1}{2}(\underline{\gamma}+\bar{\gamma})$ and check if the ARE in Equation 5 has a positive semidefinite stabilizing solution. This step can be performed in Matlab using the care command. ${ }^{\dagger}$ If such a solution exists then the state feedback gain $K:=-B_2^T X$ stabilizes the plant and achieves $\left\|F_L(G, K)\right\|_{\infty}<\gamma$. In this case redefine $\bar{\gamma}:=\gamma$. If the ARE does not have the desired solution then redefine $\underline{\gamma}:=\gamma$. In either case, the interval length has been reduced by a factor of two (i.e. bisected) and $\gamma^* \in[\underline{\gamma}, \bar{\gamma}]$.
The next of of the bisection iteration can be continued with $\gamma:=\frac{1}{2}(\underline{\gamma}+\bar{\gamma})$. This process is continued until $\bar{\gamma}-\underline{\gamma}$ is within a desired tolerance. An alternative algorithm can be formulated using the ARI in Equation 6. This leads to a class of convex optimization problems known as semidefinite programs (SDPs). These are optimization problems with a linear cost and linear matrix inequality (LMI) constraints. See text by Boyd, El Gahoui, Feron, and Balakrishnan for details.

Finally, note that the state-feedback controller was restricted to be a constant gain $K$. It is interesting that the optimal gain $\gamma^*$ is unchanged if the state-feedback controller is allowed to be a dynamic LTI system with $x$ as input and $u$ as output. It is also noted that a related "full information" problem can be formulated. This is similar to the state-feedback problem except that the controller has measurements of both the state and the disturbance $y=\left[\begin{array}{l}x \\ d\end{array}\right]$. If the direct feedthrough from disturbance to error is zero in the plant $\left(D_{11}=0\right)$ then the state feedback solution given here is still optimal, i.e. there is no benefit to the disturbance measurement. However, there is a benefit to using the disturbance measurement if $D_{11} \neq 0$. Details on these additional special cases can be found in the textbook by Zhou, Doyle and Glover.

---
${ }^{\dagger}$ In R2019a, care was replaced with icare. The new function icare uses a more numerically reliably matrix pencil formulation for solving AREs.
