---
Note Status:
  - 🌱0
Note Type:
  - 📄note
Source Type:
  - 🏫lecture
tags:
  - control
  - linear_algebra
---
# Metadata
Source URL       : [UMN/EE5235: Robust Multivariable Control Systems]
Author              : [[Nicola Elia]]
Related Note     : [[02-SystemNorms]]


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

The vector 2-norm was previously introduced to measure the "magnitude" or "length" of a complex vector. This choice led to an induced 2-norm for complex matrices. Similarly, norms can be defined on signals (functions of time) and these can be used to define induced norms for systems. Consider a real, vector-valued signal $f:[0, \infty) \rightarrow \mathbb{R}^n$. These notes will focus on the $\mathcal{L}_2$ norm as defined below:
$$
\|f\|_2:=\sqrt{\int_0^{\infty} \sum_{i=1}^n\left|f_i(t)\right|^2 d t}
$$
It is important to distinguish between the notation $\|f\|_2$ and $\|f(t)\|_2$. The first is the $\mathcal{L}_2$ norm of the signal $f$ while the second is the 2-norm of the vector $f(t) \in \mathbb{R}^n$ at time $t$. Note that the integrand in Equation 1 is $\|f(t)\|_2^2$ and thus $\|f\|_2^2=\int_0^{\infty}\|f(t)\|_2^2 d t$. In other words, the squared $\mathcal{L}_2$ norm of $f$ is given by integrating the squared 2 -norm of $f(t)$ over time. The same definition is used for complex-valued signals $f:[0, \infty) \rightarrow \mathbb{C}^n$.

It is possible that the integral in Equation 1 is not finite. ${ }^{\dagger}$ The class of $\mathcal{L}_2$ signals are those with finite $\mathcal{L}_2$ norm, i.e. $f \in \mathcal{L}_2$ if $\|f\|_2<\infty$. The more precise notation $\mathcal{L}_2^n[0, \infty)$ will occasionally be used to emphasize the vector dimension and/or the time interval of the signal. It can be verified that Equation 1 is indeed a norm on $\mathcal{L}_2$ signals, i.e. it satisfies the three axioms given previously (Positive Definiteness, Scalability, Triangle Inequality) for $\mathcal{L}_2$ signals.


