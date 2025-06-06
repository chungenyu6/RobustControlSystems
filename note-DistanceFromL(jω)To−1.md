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
Related Note     : [[02-DiskMargins]]


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

![[Pasted image 20230427132617.png|500]]

Another robustness margin is obtained by directly considering the (vector) distance between $L(j \omega)$ and the critical -1 point. The right plot of Figure 1 shows the vectors -1 and $L(j \omega)$ (black dotted). The vector between -1 and $L(j \omega)$ is given by $1+L(j \omega)$ (red solid). The minimum distance between the Nyquist plot $L(j \omega)$ to -1 is another robustness measure. This minimum distance is given by:

$$
|S(j \omega)|=\frac{1}{\mid 1+L(j \omega)}
$$
$$\|S(j \omega)\|_{\infty}=\operatorname{Sup}_\omega \frac{1}{|(+L j \omega)|}=d_{\min }:=\min _\omega|1+L(j \omega)|$$

Note that the minimum distance $d_{\min }$ can occur as $\omega \rightarrow \infty$. Thus the minimum in Equation 2 is over all finite and infinite frequencies, i.e. min over $\omega \in \mathbb{R} \cup\{+\infty\} .^{\dagger}$ If $d_{\min } \ll 1$ then $L(j \omega)$ approaches "near" to -1 at some frequency. In this case, small (gain and/or phase) variations in the plant model can cause $L(j \omega)$ to pass through -1 or cause $L(j \omega)$ to have the wrong number of encirclements. Both cases would imply that the closed-loop is unstable.

We can express this metric $d_{\min }$ in a more convenient form. First define the $\mathcal{L}_{\infty}$ norm of a (SISO) transfer function $P(s)$ as follows:
$$
\|P\|_{\infty}:=\max _\omega|P(j \omega)|
$$

The $\mathcal{L}_{\infty}$ norm for $P$ is simply the peak (largest value) of the gain across all finite and infinite frequencies. This definition is valid for stable and unstable systems. If $P$ is stable then this is also called the $\mathcal{H}_{\infty}$ norm. $\ddagger$ The definition in Equation 3 yields the relation $d_{\min }=\frac{1}{\|S\|_{\infty}}$. In other words, a large peak gain of $S$ corresponds to poor robustness, i.e. $\|S\|_{\infty} \gg 1$ implies $L(j \omega)$ comes near to -1 .

Early classical control designers were aware that gain and phase margins are related to the distance from $L$ to -1 although the actual distance is a more meaningful metric as a stability margin. However, gain and phase margins were convenient as they could be easily derived from graphical representations, e.g. a Bode plot of the open loop $L$. In contrast the distance from $L$ to -1 was more cumbersome to assess from a Bode plot of $L$. Classical designers would use gain and phase margins with care knowing that $L$ could have good gain and phase margins and yet $L$ could be near -1 . Modern design techniques have become more automated and this automation can create issues associated with less careful use of gain and phase margins. This motivates the introduction for more general robustness metrics for SISO systems (and their extensions to MIMO systems).

---
${ }^{\dagger}$ Equivalently, $d_{\min }$ can be defined as the infimum over all finite frequencies, i.e. $d_{\min }:=$ inf $\omega \in \mathbb{R}|1+L(j \omega)|$. Any use of $\min$ or max over frequency in the remainder of the notes should interpreted similarly, i.e. $\mathrm{min} / \mathrm{max}$ over $\omega \in \mathbb{R} \cup\{+\infty\}$ or inf/sup over $\omega \in \mathbb{R}$.
${ }^{\ddagger} \mathcal{L}_{\infty}$ is the space of complex functions that are measurable and essentially bounded on the imaginary axis. $\mathcal{H}_{\infty}$ is a related Hardy space consisting of functions that are holomorphic in the open left half of the complex plane.
