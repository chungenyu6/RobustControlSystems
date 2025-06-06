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


The value $s=-1$ in the complex plane is a critical point on a Nyquist plot. Consider the feedback system shown in Figure 6. Recall that the zeros of $1+L(s)$ are poles of the closed-loop system (assuming the realization for $L(s)$ is minimal). For example, the sensitivity function is $S(s)=\frac{1}{1+L(s)}$. If $1+L\left(s_0\right)=0$ for some complex $s_0$ then $\left|S\left(s_0\right)\right|=\infty$, i.e. $s_0$ is a pole of $S(s)$.

![[Pasted image 20230427113947.png | 300]]

Suppose that the Nyquist curve of the loop $L(s)$ passes through $s=-1$, i.e. there is some frequency $\omega_0$ such that $L\left(j \omega_0\right)=-1$. This can be rewritten as $1+L\left(j \omega_0\right)=0$. In other words, $1+L(s)$ has a zero at $s=j \omega_0$ and, by the discussion above, the closed-loop has pole at $s=j \omega_0$. Hence if the Nyquist curve of $L(s)$ passes through the critical point $s=-1$ then the closed-loop has a pole on the imaginary axis and therefore the closed-loop is unstable.
The value $s=-1$ also plays a critical role in the Nyquist stability condition. Recall that the feedback system is defined to be stable if all possible transfer functions in the system $(r$ to $e$, etc) are stable (Definition 3). Moreover, recall that the feedback system is unstable if there is a RHP pole/zero cancellation between $P(s)$ and $C(s)$. Thus for the remainder of the section it is assumed that there are no such RHP pole/zero cancellations in the loop transfer function $L(s)=P(s) C(s)$. With this assumption, the feedback system is stable if and only if $1+P(s) C(s)$ has no zeros in the RHP (Theorem 3). The Nyquist theorem, given below, provides a condition for stability of the closed-loop system in terms of the Nyquist plot of the (open) loop $L(s)$. The following notation is used to state the Nyquist theorem:
- $N_{C L}$ : This denotes the number of poles of the closed-loop system in the RHP (including the imaginary axis).
- $N_{O L}$ : This denotes the number of poles of the open-loop transfer function $L(s)$ in the RHP (including the imaginary axis).
- $N_{C C W}$ : This denotes the number of times the Nyquist curve of $L(s)$ encircles the critical -1 point in the counter-clockwise direction.

The Nyquist theorem is stated for the simpler case where $L(s)$ has no poles on the imaginary axis.

Theorem 4 (Nyquist Theorem). Assume $L(s)$ has no poles on the imaginary axis. Then $N_{C L}=N_{O L}-N_{C C W}$. Thus the closed-loop is stable $\left(N_{C L}=0\right)$ if and only if $N_{C C W}=N_{O L}$.
The Nyquist condition allows closed-loop stability to be determined from a Nyquist plot of the open loop $L(s)$. The Nyquist theorem (Theorem 4) as stated above assumes that $L(s)$ has no poles on the imaginary axis. This can be extended for the case where $L(s)$ has imaginary axis poles. It requires $L(s)$ to be evaluated on the imaginary axis but with indentations around the frequencies of the open loop imaginary-axis poles. The Nyquist stability theorem will mainly be used for theoretical proofs and improved understanding of robustness issues.