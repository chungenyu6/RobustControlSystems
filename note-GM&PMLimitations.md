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

Robustness margins measure how close the Nyquist plot of the (nominal) loop $L(s)=P(s) C(s)$ approaches the critical -1 point. It is assumed that the controller $C(s)$ has been designed so that the Nyquist curve of $L(s)$ encircles -1 the "correct" number of times to ensure closed-loop stability. If the Nyquist plot of $L(s)$ comes "near" to the -1 point then small variations in the model $P(s)$ can cause $L(j \omega)$ to pass through -1 or to have the wrong number of number of encirclements of -1 . Both situations would imply that the closed-loop is unstable. The classical gain and phase margins measure how close $L(j \omega)$ comes to the critical -1 point along two specific directions. Gain margins measure the closeness between $L(j \omega)$ and -1 along the negative real axis. Phase margins measure the closeness between $L(j \omega)$ and -1 along a circle of radius 1. These two directions are highlighted by red arrows in the left plot of Figure 1 . The actual (vector) distance from -1 to $L(j \omega)$ is shown on the right plot and is discussed further in the next section.

![[Pasted image 20230427132617.png|500]]

There are two important limitations to classical gain and phase margins. The first limitation is that real systems can have simultaneous gain and phase variations. Consider the Bode plot shown on the left of Figure 2. This Bode plot shows a collection of frequency responses obtained from input-output experiments on hard disk drives (blue). A low order model used for control design is also shown (yellow). The model accurately represents the experimental data at low frequencies but loses fidelity at higher frequencies. The arrows in the figure point to a range of frequencies where the model is reasonably accurate but with variations in both gain and phase relative to the experimental data. These simultaneous variations are not captured by the classical margins which only consider gain or phase variations but not both.
The second limitation is that systems may have large gain/phase margins and yet not be robust. This is illustrated with the plant $P(s)=\frac{-s+2}{2 s-1}$ and the following two controllers:*
$$
K_p=1 \text { and } K_d(s)=\frac{s+3.3}{3.3 s+1} \cdot \frac{s+0.55}{0.55 s+1} \cdot \frac{1.7 s^2+1.5 s+1}{s^2+1.5 s+1.7}
$$
The Nyquist curves for $L_p(s)=P(s) K_p$ and $L_d(s)=P(s) K_d(d)$ are shown on the right side of Figure 2. Both curves have similar phase margins. The loop $L_d(s)$ has larger gain margins than $L_p(s)$. However, the Nyquist curve of $L_d(s)$ approaches more closely to the critical -1 point and hence this feedback system is less robust. More complex examples can be constructed that have good gain/phase margins but come arbitrarily close to the -1 point.

![[Pasted image 20230427132718.png|500]]

