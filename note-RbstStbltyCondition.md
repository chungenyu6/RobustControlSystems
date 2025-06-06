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

![[Pasted image 20230427175335.png|400]]

This section provides a useful determinant condition for robust stability. Consider the uncertain system $F_U(M, \Delta)$ shown in Figure 1 [[202304271659-LFTUncertaintyModeling]]. Assume the uncertainty $\Delta$ is a stable, LTI system described by the structured set $\boldsymbol{\Delta}$. Further assume that the uncertain system is nominally stable, i.e. $M$ is stable. Let $M=\left[{ }^{M_{11}} M_{21} M_{12}\right]$ and $\Delta$ have the following state-space realizations:
$$
\begin{aligned}
\dot{x}(t) & =A x(t)+B_1 w(t)+B_2 d(t) & \dot{z}(t) & =A_{\Delta} z(t)+B_{\Delta} v(t) \\
v(t) & =C_1 x(t)+D_{11} w(t)+D_{12} d(t) & w(t) & =C_{\Delta} z(t)+D_{\Delta} v(t) \\
e(t) & =C_2 x(t)+D_{21} w(t)+D_{22} d(t) & &
\end{aligned}
$$
The matrices $\left(A_{\Delta}, B_{\Delta}, C_{\Delta}, D_{\Delta}\right)$ must also be structured to ensure $\Delta \in \boldsymbol{\Delta}$. If $\Delta$ contains only real or complex uncertainty then $\Delta$ is simply a constant matrix. In this case, $\Delta$ can be interpreted as an LTI system with only a (structured) feedthrough matrix $D_{\Delta}$ and no states.

Substitute $w=C_{\Delta} z+D_{\Delta} v$ into the output equation for $v$ and re-arrange to obtain:
$$
\left(I-D_{11} D_{\Delta}\right) v(t)=C_1 x(t)+D_{11} C_{\Delta} z(t)+D_{12} d(t)
$$
Recall that the LFT is well-posed if $I-D_{11} D_{\Delta}=I-M_{11}(\infty) \Delta(\infty)$ is nonsingular. This allows for $v$ to be expressed in terms of $(x, z, d)$. The intermediate variables $(v, w)$ can then be eliminated to obtain a state-space realization for $F_U(M, \Delta)$. The notation simplifies for the special case $D_{i j}=0(i, j=1,2)$ leading to:
$$
\begin{aligned}
{\left[\begin{array}{c}
\dot{x}(t) \\
\dot{z}(t)
\end{array}\right] } & =\left[\begin{array}{cc}
A+B_1 D_{\Delta} C_1 & B_1 C_{\Delta} \\
B_{\Delta} C_1 & A_{\Delta}
\end{array}\right]\left[\begin{array}{c}
x(t) \\
z(t)
\end{array}\right]+\left[\begin{array}{c}
B_2 \\
0
\end{array}\right] d(t) \\
e(t) & =C_2 x(t)
\end{aligned}
$$
The system $F_U(M, \Delta)$ with a particular $\Delta$ is unstable if it has a poles in the closed RHP. The next lemma gives a determinant condition for the existence of closed-RHP poles of $F_U(M, \Delta)$.

Lemma 1. Assume $M$ and $\Delta$ are stable. Also assume that the $\operatorname{LFT} F_U(M, \Delta)$ is well-posed. Then $F_U(M, \Delta)$ has a pole at $s_0$ in closed $R H P$ if and only if $\operatorname{det}\left(I-M_{11}\left(s_0\right) \Delta\left(s_0\right)\right)=0$

Proof. Let $(\bar{A}, \bar{B}, \bar{C}, \bar{D})$ denote the state-space realization for $F_U(M, \Delta)$ given in Equation 3. The poles of this system are the eigenvalues of $\bar{A}$. Thus $F_U(M, \Delta)$ has a pole at $s_0$ in the closed RHP if and only if $\operatorname{det}\left(s_0 I-\bar{A}\right)=0$. This determinant can be re-formulated using the block-determinant formula:
$$
\begin{aligned}
\operatorname{det}\left(s_0 I-\bar{A}\right) & =\operatorname{det}\left(s_0 I-A_{\Delta}\right) \cdot \operatorname{det}\left(\left(s_0 I-A-B_1 D_{\Delta} C_1\right)-B_1 C_{\Delta}\left(s_0 I-A_{\Delta}\right)^{-1} B_{\Delta} C_1\right) \\
& =\operatorname{det}\left(s_0 I-A_{\Delta}\right) \cdot \operatorname{det}\left(s_0 I-A-B_1 \Delta\left(s_0\right) C_1\right)
\end{aligned}
$$
Stability of $\Delta$ implies that $\left(s_0 I-A_{\Delta}\right)$ has a non-zero determinant and its inverse exists for any $s_0$ in the RHP. Thus $F_U(M, \Delta)$ has a pole at $s_0$ in the closed-RHP if and only if $\operatorname{det}\left(s_0 I-\right.$ $\left.A-B_1 \Delta\left(s_0\right) C_1\right)=0$. Next, apply the determinant product rule:
$$
\operatorname{det}\left(s_0 I-A-B_1 \Delta\left(s_0\right) C_1\right)=\operatorname{det}\left(s_0 I-A\right) \cdot \operatorname{det}\left(I-\left(s_0 I-A\right)^{-1} B_1 \Delta\left(s_0\right) C_1\right)
$$
Stability of $M$ implies that $\left(s_0 I-A\right)$ has a non-zero determinant and its inverse exists for any $s_0$ in the RHP. Thus $F_U(M, \Delta)$ has a pole at $s_0$ in the closed-RHP if and only if
$$
\operatorname{det}\left(I-\left(s_0 I-A\right)^{-1} B_1 \Delta\left(s_0\right) C_1\right)=0
$$

Finally, apply Sylvester's determinant theorem to shift around $C_1$ :
$$
\operatorname{det}\left(I-\left(s_0 I-A\right)^{-1} B_1 \Delta\left(s_0\right) C_1\right)=\operatorname{det}(I-\underbrace{C_1\left(s_0 I-A\right)^{-1} B_1}_{:=M_{11}\left(s_0\right)} \Delta\left(s_0\right))
$$
Thus $F_U(M, \Delta)$ has a pole at $s_0$ in the closed-RHP if and only if $\operatorname{det}\left(I-M_{11}\left(s_0\right) \Delta\left(s_0\right)\right)=0$.
The lemma implies that $F_U(M, \Delta)$ is unstable if and only if $\operatorname{det}\left(I-M_{11}\left(s_0\right) \Delta\left(s_0\right)\right) \neq 0$ for some $s_0$ in closed RHP. Thus stability of $F_U(M, \Delta)$ only depends on $\Delta$ and the upper left sub-block of $M$, i.e. $M_{11}$. This can also be seen from the LFT expression from input $d$ to output $e$ :
$$
F_U(M, \Delta)=M_{22}+M_{21} \Delta\left(I-M_{11} \Delta\right)^{-1} M_{12}
$$
The systems $\Delta$ and $M_{i j}(i, j=1,2)$ are all stable by assumption. Hence $F_U(M, \Delta)$ is unstable if and only if $\left(I-M_{11} \Delta\right)^{-1}$ is unstable. A consequence of this lemma is that the robust stability margin can be computed by finding the $\Delta \in \Delta$ with "smallest" $\|\Delta\|_{\infty}$ such that $\operatorname{det}\left(I-M_{11}\left(s_0\right) \Delta\left(s_0\right)\right)=0$ for some $s_0$ in closed RHP.
