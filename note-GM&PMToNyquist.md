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

Nyquist plots provide another interpretation for gain and phase margins. Consider a feedback system with the (nominal) open-loop $L(s)=\frac{2}{s^3+2 s^2+3 s-1}$. The poles of $L(s)$ are at $s_{1,2}=$ $-1.14 \pm 1.53 j$ and $s_3=0.28$. Thus $L(s)$ is unstable with a single pole in the RHP $\left(N_{O L}=\right.$ 1). The Nyquist curve of $L(s)$, shown on the left of Figure 9 , has a single counterclockwise encirclement of the critical -1 point $\left(N_{C C W}=1\right)$. By the Nyquist Theorem (Theorem 4), the (nominal) closed-loop has $N_{C L}=N_{O L}-N_{C C W}=0$ poles in the RHP and hence the closedloop is stable. This can be verified by directly computing the (nominal) sensitivity function: $S(s)=\frac{s^3+2 s^2+3 s-1}{s^3+2 s^2+3 s+3}$. The poles of $S(s)$ are $s_{1,2}=-0.78 \pm 1.31 j$ and $s_3=-0.43$. All poles of $S(s)$ are in the LHP and the nominal closed-loop is stable as predicted by the Nyquist theorem. Recall that a (positive) gain variation $g_0$ causes a closed-loop pole at $s= \pm j \omega_0$ if and only if $L\left(j \omega_0\right)=-\frac{1}{g_0}$. This condition implies that $\angle L\left(j \omega_0\right)= \pm 180 \operatorname{deg}$, i.e. $L\left(j \omega_0\right)$ is a real, negative number. The Nyquist curve shown in Figure 9 has two frequencies where $L(j \omega)$ is a real negative number: $\omega_1=1.73 \mathrm{rad} / \mathrm{sec}$ and $\omega_2=0 \mathrm{rad} / \mathrm{sec}$. Both frequencies are marked on the Nyquist plot and the corresponding frequency response is given in the table on the right of Figure 9. The magnitude at the first gain margin frequency is $\left|L\left(j \omega_1\right)\right| \approx 0.29$ and the corresponding critical gain is $g_1=\frac{1}{\left|L\left(j \omega_1\right)\right|}=3.5$. The magnitude at the second gain margin frequency is $\left|L\left(j \omega_2\right)\right|=2.0$ and the corresponding critical gain is $g_2=\frac{1}{\left|L\left(j \omega_2\right)\right|}=0.5$. Based on these results, the gain margins are $\bar{g}=3.5$ and $\underline{g}=0.5$.

![[Pasted image 20230427114932.png | 500]]

Next, recall that a phase variation $\theta_0$ causes a closed-loop pole at $s=j \omega_0$ if and only if $e^{-j \theta_0} L\left(j \omega_0\right)=-1$. This condition implies that $\left|L\left(j \omega_0\right)\right|=1$, i.e. $L\left(j \omega_0\right)$ intersects the disk of radius one centered at the origin (unit disk). The Nyquist curve shown in Figure 9 has one positive frequency where $L(j \omega)$ has magnitude equal to one: $\omega_1=0.49 \mathrm{rad} / \mathrm{sec}$. This frequency is marked on the Nyquist plot and the corresponding frequency response is given in the table on the right of Figure 9. The phase at the phase margin frequency is $\angle L\left(j \omega_1\right)=$ $-2.41 \mathrm{rad} \approx-137.6 \mathrm{deg}$. The corresponding critical phase is $\theta_1=\angle L\left(j \omega_1\right)+180 \mathrm{deg}=42.4 \mathrm{deg}$. Thus the phase margin is $\bar{\theta}=42.4 \mathrm{deg}$. Recall that there is a symmetry in phase margins, i.e $\theta_1>0$ causes an instability if and only if $-\theta_1$ causes instability. This symmetry appears on the Nyquist plot at the negative frequency $-0.49 \mathrm{rad} / \mathrm{sec}$. Specifically $|L(-0.49 j)|$ also has magnitude equal to one and the phase at this frequency is $\angle L(-0.49 \mathrm{j})=2.41 \mathrm{rad} \approx 137.6 \mathrm{deg}$. This yields a critical phase of $-42.4 \mathrm{deg}$. Thus the phase margin is $\bar{\theta}=42.4 \mathrm{deg}$ and the closed-loop is stable for all phase variations in the range $-\bar{\theta}<\theta<\bar{\theta}$.

The gain and phase margins mark the boundary between stable and unstable closed-loops.

![[Pasted image 20230427115031.png | 500]]

For example, a critical gain $g_i$ causes the closed-loop to have a pole on the imaginary axis at $s=$ $\pm j \omega_i$. This is equivalent to $g_i L\left(j \omega_0\right)=-1$, i.e. the Nyquist curve of $g_i L\left(j \omega_0\right)$ passes through the critical -1 point. The left plot of Figure 10 shows the Nyquist curve for the nominal loop $L(s)=\frac{2}{s^3+2 s^2+3 s-1}$ (blue) and the loop with the lower gain margin $g L(s)=0.5 L(s)$ (red dashed). The nominal loop has a single counter-clockwise encirclement of -1 as discussed above $\left(N_{C C W}=+1\right)$. This is the "correct" number of encirclements for closed-loop stability. The Nyquist curve shrinks as the gain is reduced until the curve $g L(s)$ just passes through the -1 point. This indicates that the closed-loop has a pole at $s=\bar{j} \omega_2=0 \mathrm{rad} / \mathrm{sec}$. If the gain is reduced further $(g<\underline{g})$ then the Nyquist curve of $g L(s)$ will no longer encircle the -1 point $\left(N_{C C W}=0\right)$ indicating an unstable closed-loop $\left(N_{C L}=N_{O L}-N_{C C W}=1\right)$. The right plot of Figure 10 shows similar results using the Nyquist curve for the nominal loop $L(s)$ (blue) and the loop with the upper gain margin $\bar{g} L(s)=3.5 L(s)$ (red dashed). The Nyquist curve grows as the gain is increased until the curve $\bar{g} L(s)$ just passes through the -1 point. This indicates that the closed-loop has a pole at $s=j \omega_1=1.73 \mathrm{rad} / \mathrm{sec}$. If the gain is increased further $(g>\bar{g})$ then the Nyquist curve of $g L(s)$ will encircle the -1 point once in the clockwise direction $\left(N_{C C W}=-1\right)$ indicating an unstable closed-loop $\left(N_{C L}=N_{O L}-N_{C C W}=+2\right)$. Similar results can be obtained for phase margins, i.e. the phase margin $\bar{\theta}$ causes the Nyquist curve $e^{ \pm j \bar{\theta}} L(s)$ to pass through the critical -1 point indicating the transition from stable to unstable. To summarize, gain and phase variations can cause the Nyquist curve to change from having the "correct" number of encirclements of the -1 point (stable closed-loop) to having an "incorrect" number of encirclements (unstable closed-loop).

