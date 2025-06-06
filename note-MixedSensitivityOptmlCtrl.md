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
Related Note     : [[02-MixedSensitivitySynthesis]]


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

![[Pasted image 20230427183001.png|400]]

The previous subsection formulated performance requirements in terms of frequency domain bounds: $|S| \leq\left|B_S\right|$ and $|C S| \leq\left|B_C\right|$. [[202304271821-SISORefTrackingRequirements]]. The control design amounts to finding a controller $C$ that stabilizes the plant $P$ and satisfies these bounds. It will be useful express these requirements in a normalized form. Define the "weights" $W_S:=\frac{1}{B_S}$ and $W_C:=\frac{1}{B_C}$. Note that the weights are large where the bounds are small and vice versa. The design requirements can be equivalently written as $\left\|W_S S\right\|_{\infty} \leq 1$ and $\left\|W_C C S\right\|_{\infty} \leq 1$. A block diagram interpretation is shown in Figure 3. This diagram shows the original classical feedback diagram but appended with the weights $W_S$ and $W_C$. The sensitivity requirement $\left\|W_S S\right\|_{\infty} \leq 1$ means that that gain from reference $r$ to the weighted error $\tilde{e}$ must remain $\leq 1$. Similarly, the control effort requirement $\left\|W_C C S\right\|_{\infty} \leq 1$ means that that gain from reference $r$ to the weighted control command $\tilde{u}$ must remain $\leq 1$.

Consider the following optimal control problem:
$$
\gamma^*=\min _{C \text { stabilizing }}\left\|\begin{array}{c}
W_S S \\
W_C C S
\end{array}\right\|_{\infty}
$$
In words, this optimization attempts to find a controller that stabilizes the plant and minimizes the $H_{\infty}$ norm from the single input $r$ to the two weighted outputs $\left[\begin{array}{c}\tilde{e} \\ \tilde{u}\end{array}\right]$. Let $C$ be a stabilizing controller that achieves a cost $\gamma$. Then $\left\|W_S S\right\|_{\infty} \leq \gamma$ and $\left\|W_C C S\right\|_{\infty} \leq \gamma .^{\dagger}$ Thus $\gamma^*<1$ ensures there is a stabilizing controller that achieves the performance requirements.

Other related optimal design problems can be formulated. However, this formulation is a special version of a more general formulation known as $H_{\infty}$ optimal control. This general $H_{\infty}$ optimal control will, under some technical assumptions, have several nice properties. In particular, there will be efficient conditions to compute (nearly) optimal stabilizing controllers. These (sub-)optimal controllers will be given as state-space systems with the order of $C$ less than or equal to the sum of the orders of $P, W_S$ and $W_C$. The numerical algorithms to solve the $H_{\infty}$ problem will require the weights to be stable, proper, LTI systems. In addition, the control bound must be finite at all frequencies, i.e. the corresponding weight must satisfy $\left|W_C(\mathrm{~J} \omega)\right|>0$. This places some minor technical constraints on the choices for the performance bounds and their corresponding weights. Finally, there are many generalizations to this simple mixed sensitivity formulation including MIMO systems, 2 degree-of-freedom (feedback and feedforward) control, etc. These generalizations and technical details will be be discussed in subsequent sections.

---
†This follows from basic properties of the maximum singular value. Specifically, let $M_1$ and $M_2$ be given complex matrices with the same column dimension. Then $\bar{\sigma}\left(\left[{ }_{M_1}^{M_2}\right]\right) \leq \max \left(\bar{\sigma}\left(M_1\right), \bar{\sigma}\left(M_2\right)\right)$. This can be shown using the equality between the maximum singular value and the induced matrix 2-norm.

---
## Ex
Example 1. Consider the plant $P(s)=\frac{1}{s+2}$, sensitivity bound $B_S(s)=\frac{2 s+0.01}{s+1}$, and control effort bound $B_C(s)=\frac{0.005 s+10}{s+2}$. This corresponds to the data used in Figure 2. The mixed sensitivity synthesis was solved in Matlab using the mixsyn function. The optimal performance level (within numerical tolerance) is $\gamma^*=0.69<1$. Thus there is a controller that achieves both performance requirements. This is expected since even the classical controller shown in Figure 2 achieves both requirements. The controller $C$ returned by mixsyn has 3 states. This is equal to the order of $P, W_S$ and $W_C$. Figure 4 shows the closed-loop transfer functions. The left side shows the sensitivity $S$ and bound $B_S$ (top) as well as the weighted sensitivity $W_S S$ (bottom). The top plot shows that the closed-loop sensitivity $S$ remains below the bound $B_S$, i.e. the requirement is satisfied. This corresponds to $\left\|W_S S\right\|_{\infty} \leq 1$ as shown in the bottom plot. The right side of Figure 4 shows $C S$ and bound $B_C$ (top) as well as the weighted control $W_C C S$ (bottom). Again, the performance is satisfied as demonstrated by $|C S| \leq\left|B_C\right|$ (top) or equivalently $\left\|W_C C S\right\|_{\infty} \leq 1$ (bottom). Note that there is a significant improvement on the simple classical controller used in Figure 2. The (nearly) optimal mixed sensitivity controller has higher bandwidth, better robustness, and significantly lower control effort (as measured by $S$ and $C S)$.

![[Pasted image 20230427183156.png|500]]
