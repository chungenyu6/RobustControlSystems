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
Related Note     : [[02-UncertaintyModeling]], [[02-RobustStability]]


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


![[Pasted image 20230427173831.png|400]]

Based on the previous notes, systems with one or more sources of uncertainty can be represented by $F_U(M, \Delta)$ where $M$ is an LTI system (Figure 1 ). The uncertainty $\Delta$ is can be structured and contain the basic atoms of real parametric (scalar) uncertainty, complex (scalar or matrix) uncertainty, and/or dynamic (scalar or matrix) LTI uncertainty. Moreover, real and complex scalar uncertainties can appear in multiple copies. ${ }^{\dagger}$ The uncertainty is described, in general, by a structured, block-diagonal set. Let $\Delta$ define the structure of the uncertainties appearing in a particular system.
1. $\Delta:=\left\{\left[\begin{array}{cc}\delta_1 & 0 \\ 0 & \Delta_2(s)\end{array}\right]: \delta_1 \in \mathbb{C}, \Delta_2\right.$ LTI, stable $\}:$ This is an uncertainty set consisting of a scalar complex uncertainty and a dynamic, LTI uncertainty.
2. $\Delta:=\left\{\left[\begin{array}{cc}\Delta_1 & 0 \\ 0 & \delta_2 I_3\end{array}\right]: \Delta_1 \in \mathbb{C}^{3 \times 2}, \delta_2 \in \mathbb{R}\right\}$ : This is an uncertainty set consisting of a matrix complex uncertainty and a scalar real parameter repeated three times.
3. $\Delta:=\left\{\left[\begin{array}{ccc}\delta_1 & 0 & 0 \\ 0 & \Delta & 0 \\ 0 & 0 & 0 \\ 0 & 0 & \delta_3 I_4\end{array}\right]: \delta_1, \delta_3 \in \mathbb{C}, \Delta_2\right.$ LTI, stable, and $\left.2 \times 2\right\}:$ This is an uncertainty set consisting of two scalar complex uncertainties (one of which is repeated four times) and a $2 \times 2$ dynamic LTI uncertainty

These sets are simply examples and, in general, the uncertainty set can contain any number and combination of the basic atoms. The uncertainty set is called "unstructured" if it consists of a single complex uncertainty, i.e. $\boldsymbol{\Delta}=\mathbb{C}^{n_w \times n_v}$, or a single (scalar or matrix) LTI, dynamic uncertainty. Typically, the uncertainty has been normalized so that all entries are norm-bounded by one. In other words, the set of modeled uncertainties corresponds to $\mathbf{B}_{\Delta}:=\{\Delta \in$ $\left.\Delta:\|\Delta\|_{\infty} \leq 1\right\} . \ddagger$ The nominal dynamics correspond to $\Delta=0$.


---
‡If $\Delta$ is block diagonal then $\|\Delta\|_{\infty} \leq 1$ if and only if the individual blocks are norm-bounded by one. Moreover, the $H_{\infty}$ norm of a constant (real or complex) block corresponds to its maximum singular value. For repeated real or complex blocks this gives $\bar{\sigma}\left(\delta I_n\right)=|\delta|$.

---
## Ex
![[Pasted image 20230427173955.png|400]]

Example 1. Consider the MIMO feedback system in Figure 2 with an $n_y \times n_u$ plant $P$ and a $n_u \times n_y$ controller $C$. The plant has a multiplicative uncertainty: $P=P_0\left(I_{n_u}+W \Delta\right)$. Consider two possible uncertainty models:
1. Complex Uncertainty: $\Delta \in \mathbb{C}^{n_u \times n_u}$ is the normalized uncertainty, $\bar{\sigma}(\Delta) \leq 1$. The matrix $W \in \mathbb{R}^{n_u \times n_u}$ is chosen to represent a specified level of uncertainty, e.g $W=0.5 I_{n_u}$ represents $50 \%$ cross-coupled uncertainty in all channels. The uncertain closed-loop system from input $r$ to output $e$ is represented by the $\operatorname{LFT} F_U(M, \Delta)$ where:
$$
\left[\begin{array}{l}
v \\
e
\end{array}\right]=\underbrace{\left[\begin{array}{cc}
C P_0\left(I_{n_u}+C P_0\right)^{-1} W & C\left(I_{n_y}+P_0 C\right)^{-1} \\
P_0\left(I_{n_u}+C P_0\right)^{-1} W & \left(I_{n_y}+P_0 C\right)^{-1}
\end{array}\right]}_{:=M}\left[\begin{array}{l}
w \\
r
\end{array}\right]
$$
$M$ can be rewritten in terms of input/output sensitivities as $M=\left[\begin{array}{cc}T_I W & C S_O \\ P_0 S_I W & S_O\end{array}\right]$. The uncertainty set is unstructured: $\Delta=\mathbb{C}^{n_u \times n_u}$. The set of modeled uncertainties corresponds to $\mathbf{B}_{\Delta}:=\{\Delta \in \Delta: \bar{\sigma}(\Delta) \leq 1\}$. This specific uncertain system $F_U(M, \Delta)$ was considered in the introduction to MIMO robustness with $W=I$.
2. Dynamic Uncertainty: $\Delta$ is an $n_u \times n_u$ stable, LTI system with $\|\Delta\|_{\infty} \leq 1$. The weight $W$ can now be an $n_u \times n_u$ system whose magnitude represents a specified level of uncertainty as a function of frequency. For example, in the scalar case, $W(s):=\frac{2 s+1}{s+10}$ represents $10 \%$ dynamic uncertainty at low frequencies and rising to $200 \%$ at high frequencies. The uncertain closed-loop system from input $r$ to output $e$ is again represented by the LFT $F_U(M, \Delta)$ with $M$ as defined in Equation 1. The uncertainty set is unstructured: $\boldsymbol{\Delta}$ corresponds to $n_u \times n_u$ stable, LTI systems. The set of modeled uncertainties corresponds to $\mathbf{B}_{\Delta}:=\left\{\Delta \in \Delta:\|\Delta\|_{\infty} \leq 1\right\}$. This type of plant uncertainty was considered when discussing dynamic, LTI uncertainty.

We will show later that complex and dynamic, LTI uncertainty describe, more or less, equivalent uncertainty sets for the purposes of robustness analysis.

---
![[Pasted image 20230427174046.png|400]]

Example 2. Figure 3 illustrates the use of multi-loop disk margins for a $2 \times 2$ MIMO plant. Scalar perturbations $\alpha_1$ and $\alpha_2$ are introduced at the two input channels of the plant. The multi-loop disk margin is defined to be the largest $m \in[0,1]$ such that the feedback loop is stable for all $\alpha_1, \alpha_2 \in \operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$. The perturbations can be expressed as $\alpha_i=\frac{1+\delta_i}{1-\delta_i}$ where $\delta_i \in \mathbb{C}$ satisfies $\left|\delta_i\right| \leq m$. Recall that this can be expressed as the LFT $\alpha_i=F_U\left(\left[\begin{array}{cc}1 & \sqrt{2} \\ \sqrt{2} & 1\end{array}\right], \delta_i\right)$. With some block diagram manipulation, the uncertain closed-loop system from input $r=\left[{ }^{r_1}\right]$ to output $e=\left[\begin{array}{l}e_1 \\ e_2\end{array}\right]$ is represented by the $\operatorname{LFT} F_U(M, \Delta)$. This manipulation is tedious but can be performed numerically.

The uncertainty set is structured: $\boldsymbol{\Delta}=\left\{\left[\begin{array}{cc}\delta_1 & 0 \\ 0 & \delta_2\end{array}\right]: \delta_1, \delta_2 \in \mathbb{C}\right\}$. The set of modeled uncertainties corresponds to $\mathbf{B}_{\Delta}:=\left\{\Delta \in \boldsymbol{\Delta}:\left|\delta_i\right| \leq 1, i=1,2\right\}$. This set of modeled uncertainties corresponds to $\operatorname{Re}\left\{\delta_i\right\} \geq 0$. The multi-loop disk margin $m$ corresponds to the subset $\left|\delta_i\right| \leq m$, i.e. $\alpha_i \in \operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$, for which stability is retained.

---
![[Pasted image 20230427174207.png|500]]

Example 3. Consider an LTI system $P(s)$ that depends on two uncertain real parameters $a \in[1,3]$ and $b \in[3.5,4.5]$. The nominal parameters values are $\left(a_0, b_0\right)=(2,4)$. The uncertain system is defined as $P(s)=\frac{1}{s^2+c_1 s+c_2}$ where:
$$
\begin{aligned}
& c_1:=4-(a-2)^2-4(b-4)^2 \\
& c_2:=1+(a-2)+2(b-4)+4(b-4)(a-2)
\end{aligned}
$$
The uncertain system has an LFT representation $F_U(M(s), \Delta)$ with the $\Delta$ in the structured set $\boldsymbol{\Delta}:=\left\{\left[\begin{array}{cc}\delta_a I_3 & 0 \\ 0 & \delta_b I_3\end{array}\right]: \delta_a, \delta_b \in \mathbb{R}\right\}$. Both $\delta_a$ and $\delta_b$ are repeated three times in this structured set. These repetitions arise because the coefficients $c_1$ and $c_2$ have a polynomial dependence on $(a, b)$. The modeled uncertainty corresponds to the normalized set $\mathbf{B}_{\boldsymbol{\Delta}}:=$ $\left\{\left[\begin{array}{cc}\delta_a I_3 & 0 \\ 0 & \delta_b I_3\end{array}\right]: \delta_a, \delta_b \in[-1,1]\right\} . M(s)$ is a $7 \times 7$ stable, LTI system. The nominal input/output dynamics are given by $F_U(M(s), 0)$ and correspond to the stable system $P_0(s)=\frac{1}{s^2+4 s+1}$.
This system only has two real parameter uncertainties. This allows for a graphical interpretation for the set of modeled uncertainty. The left plot in Figure 4 shows the set of modeled uncertainty $(a, b) \in[1,3] \times[3.5,4.5]$ (black rectangle) and the nominal value $\left(a_0, b_0\right)=(2,4)$ (black dot). The right plot is similar but in terms of the normalized uncertainties $\left(\delta_a, \delta_b\right) \in[-1,1] \times[-1,1]$ (black rectangle) and the nominal value $\left(\delta_{b 0}, \delta_{b 0}\right)=(0,0)$ (black dot). The set of modeled uncertainty corresponds to the unit cube in normalized values.
The use of normalized values allows for statements that directly scale both $a$ and $b$. For example, $50 \%$ of the modeled uncertainty corresponds to $\left(\delta_a, \delta_b\right) \in[-0.5,0.5] \times[-0.5,0.5]$. This scales down the actual uncertainty intervals to half of their modeled value, i.e. $a \in[1.5,2.5]$ and $b \in[3.75,4.25]$. Similarly, $150 \%$ of the modeled uncertainty corresponds to $\left(\delta_a, \delta_b\right) \in$ $[-1.5,1.5] \times[-1.5,1.5]$. This scales up the actual uncertainty width to $1.5 \times$ their modeled value, i.e. $a \in[0.5,3.5]$ and $b \in[3.25,4.75]$. These two scaled uncertainty levels are shown as dashed red curves in the left and right plots of Figure 4 .