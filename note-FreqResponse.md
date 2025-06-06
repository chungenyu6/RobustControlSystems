---
Note Status:
  - 🔅1
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
Related Note     : [[02-LTISystems]] 

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


The term frequency (or sinusoidal) response refers to the forced response of the system $P$ with a sinusoidal input, e.g. $u(t)=\sin (\omega t)$ or $u(t)=\cos (\omega t)$ where $\omega \in \mathbb{R}$ is a given frequency in $\frac{\mathrm{rad}}{\text { sec }}$. The forced response as $t \mapsto \infty$ is of particular interest. This is typically called the steady-state steady-state frequency response. In particular, the response depends on the transfer function evaluated at a purely imaginary number $s=j \omega$. The result $P(j \omega)$ is a complex number that can be expressed either in Cartesian form by its real/imaginary parts or in polar form by its magnitude $|P(j \omega)|$ and phase $\angle P(j \omega)$. 
Assume $P$ is a stable system. If the input is $u(t)=\bar{\mu} \sin (\omega t+\theta)$ for some real numbers $(\omega, \bar{u}, \theta)$ then the steady-state response is
$$
\begin{aligned}
& y(t) \rightarrow \bar{u}|P(j \omega)| \sin (\omega t+\theta+\angle P(j \omega)) \text { as } t \rightarrow \infty .
\end{aligned}
$$
In other words, the output amplitude is simply the input amplitude multiplied by $|P(j \omega)|$. Moreover, the output phase is simply the input phase plus the additional phase $\angle P(j \omega)$.
The steady-state sinusoidal response of a linear system is described by the frequency response function $P(j \omega)$. There are several graphical plots that can be used to understand and analyze the frequency response:
-  Bode Plot
- Nyquist Plot
