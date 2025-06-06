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

Figure 1 shows a feedback system with a plant $P$ and controller $C$. Assume $P$ is $n_y \times n_u$ and $C$ is $n_u \times n_y$. The loop signals are assumed to have compatible dimensions. These are defined as the reference command $r$, tracking error $e$, control command $u$, input disturbance $d$, plant input $v$, plant output $y$, sensor noise $n$, and measured plant output $m$. This feedback architecture is called single degree-of-freedom (DOF) because the controller only has access to the tracking error. A two DOF architecture is one where the controller has both the reference and the measurement as inputs. This can be used to model cases where the controller has both feedback and feedforward. This section will consider the single DOF architecture shown in Figure 1 but more general feedback structures, including two DOF controllers, will be considered later.

![[Pasted image 20230427145417.png|400]]

For SISO plants, the sensitivity and complementary sensitivity are defined as $S:=\frac{1}{1+L}$ and $T:=\frac{L}{1+L}$ where $L:=P C$ is the (open) loop transfer function. Any input/output transfer function in a SISO loop is one of the following transfer functions: $S, T, C S$, and $P S$. For MIMO plants, $P C$ is not, in general, equal to $C P$ because matrix multiplication does not commute. As a result, it is important to distinguish between transfer functions at the input or output of the plant $P$. For example, the transfer function from $r$ to $e$ can be computed by setting $d=0$ and $n=0$. In this case $E(s)=R(s)-P(s) C(s) E(s)$ and solving for $E(s)$ yields
$$
E(s)=\underbrace{\left(I_{n_y}+P(s) C(s)\right)^{-1}}_{:=S_O(s)} R(s)
$$
$S_O$ is the $n_y \times n_y$ output sensitivity. As another example, the transfer function from $d$ to $v$ can be computed by setting $r=0$ and $n=0$. In this case $V(s)=D(s)-C(s) P(s) V(s)$ and solving for $V(s)$ yields
$$
V(s)=\underbrace{\left(I_{n_u}+C(s) P(s)\right)^{-1}}_{:=S_I(s)} D(s)
$$
$S_I$ is the $n_u \times n_u$ input sensitivity.

Define the (open) loop at the plant input and output as $L_I:=C P$ and $L_O:=P C$. The input and output sensitivities are $S_I=\left(I_{n_u}+L_I\right)^{-1}$ and $S_O=\left(I_{n_y}+L_O\right)^{-1}$. Moreover, the input and output complementary sensitivities are
$$
\begin{aligned}
T_I & =\left(I_{n_u}+L_I\right)^{-1} L_I=L_I\left(I_{n_u}+L_I\right)^{-1} \\
T_O & =\left(I_{n_{\Downarrow}}+L_O\right)^{-1} L_O=L_O\left(I_{n_{\Downarrow}}+L_O\right)^{-1}
\end{aligned}
$$
Any input/output pair in a MIMO feedback system is one of the following six transfer functions: $S_I, S_O, T_I, T_O, C S_O$, and $P S_I$. Moreover, the relations $S_I+T_I=I_{n_{\bar{\mu}}}$ and $S_O+T_O=I_{n_\psi}$ place fundamental constraints on the performance at the plant input and output.

The output sensitivity $S_O$ is obtained above by solving $E(s)=R(s)-P(s) C(s) E(s)$ for $E(s)$. It is possible that $S_O$ is not proper even if $P$ and $C$ are proper systems. For example, let $P(s)=\frac{2 s+1}{s+1}$ and $K=-\frac{1}{2}$. Then the (SISO) sensitivity is $S(s)=\frac{1}{2}(s+1)$. This is not proper even though $P$ and $K$ are proper. Non-proper systems can not be represented with state-space models (they require a descriptor representation). The focus will be on well-posed feedback systems, as defined next, in order to avoid such situations.

Definition 1. The feedback system is defined to be well-posed if all possible transfer functions in the system ( $r$ to $e, d$ to $u, n$ to $y$, etc) are well-defined and proper.

It can be shown that the output sensitivity is well defined if and only if $I+P(\infty) C(\infty)$ is nonsingular. ${ }^{\dagger}$ Similarly, the input sensitivity is well defined if and only if $I+C(\infty) P(\infty)$ is nonsingular. These two conditions are equivalent. Moreover, products (i.e. serial interconnections) of well-defined, proper systems are proper. Thus if $S_O$ and $S_I$ are proper then $T_I$, $T_O, P S_I$ and $C S_O$ are all proper. In summary, the feedback system is well-posed if and only if $I+P(\infty) C(\infty)$ is nonsingular. Additional details can be found in Chapter 5 of Zhou, Doyle, and Glover.

Next, the stability of the MIMO feedback system is defined below. This definition is identical to that used for a SISO feedback system.

Definition 2. The feedback system is defined to be stable if all possible transfer functions in the system ( $r$ to $e, d$ to $u, n$ to $y$, etc) are stable.

---
†The output sensitivity is obtained by solving $(I+P(s) C(s)) E(s)=R(s)$ for $E(s)$. Let $P$ and $C$ have statespace representations $\left(A_P, B_P, C_P, D_P\right)$ and $\left(A_C, B_C, C_C, D_C\right)$. A state-space representation for $I+P(s) C(s)$ has the feedthrough "D" matrix $I+D_P D_C$. The system $I+P(s) C(s)$ can be inverted to obtain a proper state-space realization if and only if $I+D_P D_C$ is nonsingular.