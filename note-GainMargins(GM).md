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
Related Note     : [[02-StbltyMargins&Rbstness]]


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


The model used for control design is only an approximation for the "real" dynamics of the plant. Control engineers have developed different types of "safety factors" to account for the mismatch between the design model and the dynamics of the real system. This section will discuss one type of safety factor called the gain margin. The gain margin is the amount of allowable variation in the gain of the plant before the closed-loop becomes unstable. To make this concrete, consider the feedback diagram shown in Figure 7. $P(s)$ is the "nominal" model used to design the controller $C(s)$. The constant $g$ is introduced to represent variations in the gain of the plant dynamics. In other words, the model used for design is $P(s)$ but the real dynamics might have a different gain as represented by $g P(s)$. Typically we assume that the gain of the design model at least has the correct sign and hence only positive gain variations $g>0$ are of interest. The loop transfer function, including this gain variation, is given by $L_g(s)=g P(s) C(s)$. Note that the nominal loop transfer function corresponds to $g=1$ and this is denoted as $L(s)=P(s) C(s)$.

![[Pasted image 20230427114145.png | 400]]

Assume that the controller has been designed to stabilize the nominal design model $P(s)$, i.e. the closed-loop system is stable for $g=1$. The closed-loop system may become unstable as the gain $g$ is varied (either increased or decreased from $g=1$ ). The gain margin specifies the minimum and maximum variation for which the closed-loop remains stable as defined below.
Definition 4 (Gain Margin). The gain margin consists of an upper limit $\bar{g} \geq 1$ and a lower limit $\underline{g} \leq 1$ such that:
1. the closed-loop is stable for all positive gain variations $g$ in the range $\underline{g}<g<\bar{g}$, and
2. the closed-loop is unstable for gain variations $g=\bar{g}$ (if $\bar{g}<\infty$ ) and also unstable for gain variations $g=\underline{g}$ (if $\underline{g}>0$ ).

Thus the gain margins $\bar{g}$ and $\underline{g}$ correspond to the variations that lie at the boundary between stable and unstable closed-loops. In some cases the closed-loop remains stable for arbitrarily large increases and/or decreases in the gain $g$. The upper limit is $\bar{g}=+\infty$ if the closed-loop remains stable for any gain $g>1$. The lower limit is $\underline{g}=0$ if the closed-loop remains stable for any positive gain $g<1$. As a rule of thumb, the gain margin limits should satisfy $\bar{g}>2$ and $\underline{g}<2$ for good robustness to model uncertainty. This is frequently stated as $\pm 6 d B$ of required gain margin for good robustness. This rule of thumb is a good starting point but requirements may differ depending on the specific problem.

The gain margin for a feedback system can be determined from a Bode plot of the (open-loop) transfer function $L(s)$. Assume the nominal closed-loop is stable, i.e. all poles of $S(S)$ are in the LHP. The gain variations $g$ cause the closed-loop poles to move continuously in the complex plane. It is possible for the closed-loop poles to move into the RHP (unstable closed loop) if the gain $g$ is increased or decreased by a sufficiently large amount. The critical gains are values of $g$ for which the closed-loop poles are on the imaginary axis. These gains mark the transition as poles move from the LHP (stable) into the RHP (unstable). To be concrete, a critical gain $g_0$ causes the closed-loop to have a pole on the imaginary axis $s= \pm j \omega_0$ for some frequency $\omega_0 \geq 0$. Thus the sensitivity $S_{g 0}(s)=\frac{1}{1+g_0 L(s)}$ has poles at $s= \pm j \omega_0$ which is equivalent to $1+g_0 L\left(j \omega_0\right)=0$ (Theorem 3 ). To summarize, a (positive) gain variation $g_0$ causes a closed-loop pole at $s= \pm j \omega_0$ if and only if $L\left(j \omega_0\right)=-\frac{1}{g_0}$.

The condition for critical gains can be used to calculate the gain margin directly from the Bode plot of $L(s)$. Specifically, the condition $L\left(j \omega_0\right)=-\frac{1}{g_0}$ for some positive gain $g_0$ implies that $\angle L\left(j \omega_0\right)= \pm 180 \mathrm{deg}$. The gain margins are computed from a Bode plot as follows:
1. Identify the frequencies $\left\{\omega_1, \ldots, \omega_N\right\}$ where $\angle L\left(j \omega_i\right)= \pm 180 \mathrm{deg}$. These are called the phase crossing frequencies or gain margin frequencies. There may be zero, one, or many gain margin frequencies.
2. The associated critical gain for each frequency $\omega_i$ is $g_i=\frac{1}{\left|L\left(j \omega_i\right)\right|}(i=1, \ldots, N)$. This critical gain $g_i$ results in a closed-loop pole at $s= \pm j \omega_i$.
3. The upper gain margin $\bar{g}$ is the smallest of the critical gains above 1 . The lower gain margin $\underline{g}$ is the largest of the critical gains below 1. For example if the nominal closed-loop is stable and the critical gains are $\{0.4,0.8,1.5,2.0\}$ then the closed-loop is stable for all gains in the range $\underline{g}=0.8<g<1.5=\bar{g}$.