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
Related Note     : [[02-LTISystems]], [[02-MIMORobustness]], [[02-SystemNorms]]


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

It was shown above that a stable LTI system $P$ with (complex) input $u(t)=\bar{u} e^{j \omega t}$ will converge in steady-state to the output $y(t)=\bar{y} e^{j \omega t}$ where $\bar{y}:=P(j \omega) \bar{u}$. This can also be interpreted in terms of real sinusoidal signals. Thus the transfer function completely determines the sinusoidal response. Moreover, $\bar{\sigma}(P(j \omega))$ provides the largest gain from input amplitude $\bar{u}$ to output amplitude $\bar{y}$ at frequency $\omega$. This follows from Theorem 2.

For a MIMO system, the transfer function $P(s)$ is an $n_y \times n_u$ array of scalar transfer functions. An array of Bode plots can be generated to display the magnitude and phase for each entry of $P(s)$. This provides useful information but is cumbersome if the system has many inputs and/or outputs. An alternative is a singular value plot (or $\sigma$-plot) of $P$. This consists of a single plot displaying the singular values for the complex matrix $P(j \omega)$ as a function of frequency. The horizontal axis is frequency $\omega$ on a $\log$ (base 10) scale. This is typically in units of $\frac{\text { rad }}{s e c}$ although it can also appear in other units, e.g. $H z$. The vertical axis are the singular values expressed in units of decibels, i.e. $\left|\sigma_i(P(j \omega))\right|_{d B}$. This single plot provides additional insight into the coupling and gain of a MIMO system across frequencies. Figure 2 shows an example singular value plot for the following two-input, two-output system:
$$
S(s):=\left[\begin{array}{cc}
\frac{s}{s+3} & \frac{-6 s}{s^2+6 s+9} \\
0 & \frac{s}{s+3}
\end{array}\right]
$$

![[Pasted image 20230427143341.png|400]]

The peak on the singular value plot for a (MIMO) transfer function $P(s)$ is:
$$
\|P\|_{\infty}:=\max _\omega \bar{\sigma}(P(j \omega))
$$
This definition gives the maximum gain of the frequency response of $P$. It involves a maximum over the input amplitude (due to the equality $\left.\bar{\sigma}(P(j \omega))=\|P(j \omega)\|_{2 \rightarrow 2}\right)$ as well as the maximum over frequency. For SISO systems, $\bar{\sigma}(P(j \omega))=|P(j \omega)|$ and hence Equation 20 is equivalent to the $\mathcal{L}_{\infty}$ norm defined previously as the peak on a Bode plot. As before, the definition in Equation 20 is valid for stable and unstable systems. In other words, $\|P\|_{\infty}$ is finite as long as $P$ has no poles on the imaginary axis so that $P(j \omega)$ is uniformly bounded. If $P$ is stable then this is also called the $\mathcal{H}_{\infty}$ norm (although this notation/term is sometimes used even if $P$ is not necessarily stable). As an example, the system in Equation 19 is stable. It has $\mathcal{H}_{\infty}$ norm given by $\|S\|_{\infty}=1.414=3 d B$. The peak gain occurs at the frequency $\omega_p=4.35$ $\mathrm{rad} / \mathrm{sec}$.


