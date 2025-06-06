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

This section provides a solution to the $H_{\infty}$ output-feedback problem. Consider the linear time-invariant system $G$ :
$$
\begin{aligned}
\dot{x}(t) & =A x(t)+B_1 d(t)+B_2 u(t) \\
e(t) & =C_1 x(t)+D_{12} u(t) \\
y(t) & =C_2 x(t)+D_{21} d(t)
\end{aligned}
$$
Let $\gamma>0$ be given. The goal is to design a (dynamic) output feedback controller $K(s)$ such that $u=K x$ stabilizes $F_L(G, K)$ and achieves $\left\|F_L(G, K)\right\|_{\infty}<\gamma$ or determine that no such gain exists. The controller $K$ is assumed to be LTI but no assumption is made, a priori regarding its state dimension. Assume $G$ satisfies the following assumptions:
1. $\left(A, B_2\right)$ is stabilizable: This ensures that there is a feedback gain that stabilizes the plant $G$.
2. $(A, C 2)$ is detectable: This ensures that the unstable modes are observable in the measurements.
3. $D_{11}=0, D_{22}=0, D_{12}^T C_1=0_{n_u \times n_x}, D_{12}^T D_{12}=I_{n_u}, B_1 D_{21}^T=0_{n_x \times n_y}$, and $D_{21} D_{21}^T=I_{n_y}$ : These assumptions on the feedthrough matrix simplify the derivation. These assumptions can be relaxed.
4. Additional technical assumptions to ensure the transfer functions from $u$ to $e$ and $d$ to $y$ have no zeros on the imaginary axis (including at infinite frequency). These assumptions ensure that the control effort is penalized at all frequencies and that all measurements contain some noise.

The next theorem provides ARE conditions for the $H_{\infty}$ output feedback synthesis problem (See DGKF paper for details). There are also equivalent ARI conditions (See paper by Gahinet and Apkarian).

Theorem 2. Consider the linear time-invariant system $G$ given in Equation ?? and satisfying assumptions 1-4 above. Let $\gamma>0$ be given. The following statements are equivalent:
1. There exists a feedback controller $K$ such that $F_L(G, K)$ is stable and $\left\|F_L(G, K)\right\|_{\infty}<\gamma$.
2. There following conditions are satisfied:
(a) There exists a unique $X \geq 0$ such that $A+\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) X$ is Hurwitz and satisfying the ARE:
$$
A^T X+X A+C_1^T C_1+X\left(\gamma^{-2} B_1 B_1^T-B_2 B_2^T\right) X=0
$$
(b) There exists a unique $Y \geq 0$ such that $A+\left(\gamma^{-2} C_1^T C_1-C_2^T C_2\right) Y$ is Hurwitz and satisfying the ARE:
$$
A^T Y+Y A+B_1 B_1^T+Y\left(\gamma^{-2} C_1^T C_1-C_2^T C_2\right) Y=0
$$
(c) $\rho(X Y)<\gamma^2$ where $\rho$ denotes the spectral radius.
Moreover, if the ARE conditions are satisfied then a feasible controller is given by:
$$
\begin{aligned}
& \dot{x}_K(t)=A_K x_K(t)-Z_K L_K y(t) \\
& u_K(t)=F_K x_K(t)
\end{aligned}
$$
where
$$
\begin{aligned}
A_K & =A+\gamma^{-2} B_1B_1^T X+B_2 F_K+Z_K L_K C_2 \\
F_K & =-B_2^T X \\
L_K & =-Y C_2^T \\
Z_K & =\left(I-\gamma^{-2} Y X\right)^{-1}
\end{aligned}
$$
Note that a feasible controller can be constructed with the same state dimension as the plant $G$. This controller has an interesting observer/feedback gain structure. See details in Skogestad and Postlethwaite.
