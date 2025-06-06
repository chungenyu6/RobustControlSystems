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

Loop-at-a-time analysis is a simple extension of classical margins to assess the robustness of a MIMO feedback system. The procedure is illustrated for a $2 \times 2$ MIMO plant as shown in Figure 2. A scalar (gain, phase, or disk) perturbation $\alpha_1$ is introduced at the first input of the plant $P$. The other loop is left at its nominal (unperturbed) value. First, break the loop at the location of the perturbation as shown on the left side of Figure 3. Next, compute the transfer function from the scalar input $z_1$ to the scalar output $w_1$ (with the other loop closed as shown). Denote this SISO open loop transfer function as $-B_{I, 1}$. The subscript of $B_{I, 1}$ reflects that the loop was broken at the first channel on the input side of $P$. The perturbation $\alpha_1$ closes the loop from $w_1$ to $z_1$. Hence the MIMO feedback with perturbation at the first input of $P$ can be re-drawn as the SISO feedback system shown on the right side of Figure 3. The (gain, phase, or disk) margin associated with this loop can be computed using the SISO methods discussed previously. This gives the margin associated with the first input of $P$. These steps can be repeated to compute the margin at the second input of $P$ as well as at both outputs of $P$.

![[Pasted image 20230427145621.png|500]]

In general, loop-at-a-time margins are computed by breaking one loop with all other loops closed. If the plant is $n_y \times n_u$ then this gives $n_u$ margins at the inputs of $P$ and $n_y$ margins at the outputs of $P$. A typical rule of thumb is to require each loop margin to have at least $\pm 6 \mathrm{~dB}$ of gain margin, $45^{\circ}$ of phase margin, and $\pm 6 \mathrm{~dB}$ of (symmetric) disk margin. Unfortunately, the loop-at-a-time margins can be overly optimistic. In particular, a MIMO feedback system can have large loop-at-a-time margins and yet be destabilized by small perturbations acting simultaneously on multiple channels. An example is provided below to demonstrate this situation. This motivates the development of more advanced robustness analysis tools.

Example 1. Consider a feedback system with the following plant and controller with $a=10$ :
$$
P(s):=\frac{1}{s^2+a^2}\left[\begin{array}{cc}
s-a^2 & a(s+1) \\
-a(s+1) & s-a^2
\end{array}\right] \text { and } C(s):=\left[\begin{array}{ll}
1 & 0 \\
0 & 1
\end{array}\right]
$$
This example is taken from a 1978 CDC paper by Doyle. The dynamics represent a simplified model for a spinning satellite. Additional details can be found in Section 3.7 of Skogestad and Postlethwaite or Section 9.6 of Zhou, Doyle and Glover.

Breaking the loop at the first input of $P$ yields the SISO open loop transfer function $B_{I, 1}=\frac{1}{s}$. This loop has no $180^{\circ}$ phase crossover frequencies so the classical gain margin is $[0, \infty)$. This loop has a single gain crossover at $\omega=1 \mathrm{rad} / \mathrm{sec}$ which gives a classical phase margin of $\pm 90^{\circ}$. Finally, the SISO loop $B_{I, 1}(s)$ corresponds to the sensitivity $S_{I, 1}(s)=\frac{s}{s+1}$ and complementary sensitivity $T_{I, 1}(s)=\frac{}{s+1}$. The symmetric disk margin is $m=\frac{1}{\|S-T\|_{\infty}}=1$. This corresponds to a disk covering the entire RHP, i.e. stability is maintained for any combination of gain/phase such at $\operatorname{Re}\left\{\alpha_1\right\}>0$. These results demonstrate that the MIMO feedback system is very robust to perturbations at the first input of $P$ assuming all other inputs/outputs remain at their nominal value. Breaking the loop at the second input of $P$ or either output of $P$ yields the same open loop transfer function $B_{I, 2}(s)=B_{O, 1}(s)=B_{O, 2}(s)=\frac{1}{s}$. Again, the loop-at-atime analysis demonstrates the MIMO feedback system is very robust to perturbations at any single input or output of $P$ assuming all other inputs/outputs remain at their nominal value. Consider the following small simultaneous perturbation at both input channels of the plant:
$$
\alpha_1=0.9 \text { and } \alpha_2=1.1
$$
These perturbations to both input channels destabilize the MIMO feedback system. The loop-at-a-time margins fail to capture such simultaneous variations in multiple channels. As a consequence, the loop-at-a-time margins provide an overly optimistic assessment of the system robustness.

