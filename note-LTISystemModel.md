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

Consider a continuous-time, linear time-invariant system (LTI) $P$ with input $u$ and output $y$ as shown in Figure 1. Assume, for the moment, that $P$ is **single-input, single-output (SISO)**. Thus the input signal $u: \mathbb{R}{\geq 0} \rightarrow \mathbb{R}$ and output signal $y: \mathbb{R}{\geq 0} \rightarrow \mathbb{R}$ are scalar functions of time.

![[Pasted image 20230422170905.png | 300]]

There are different models that can be associated with this dynamical system. The dominant representation used in classical controls is given by an $n^{\text {th }}$ order, ordinary differential equation $(\mathrm{ODE})^{\dagger}$ :
$$
\begin{gathered}
y^{[n]}(t)+a_{n-1} y^{[n-1]}(t)+\cdots+a_1 \dot{y}(t)+a_0 y(t)=b_m u^{[m]}(t)+\cdots+b_1 \dot{u}(t)+b_0 u(t) \\
\text { Initial Conditions (ICs): } y(0):=y_0, \ldots, y^{[n-1]}(0)=y_0^{[n-1]}
\end{gathered}
$$
The transfer function is a complex function $P: \mathbb{C} \rightarrow \mathbb{C}$ with rational dependence on $s \in \mathbb{C}$. Note that $P$ is used to denote both the system and its corresponding transfer function. The **denominator** is an $n^{\text {th }}$ order polynomial that defines the following **characteristic equation**:
$$
s^n+a_{n-1} s^{n-1}+\cdots a_1 s+a_0=0
$$
The <u>characteristic equation has $n$ roots</u>, denoted $\left\{p_k\right\}_{k=1}^n \subset \mathbb{C}$, and these roots are called the **poles of the system**. Similarly, the <u>roots of the numerator of </u> $P(s)$ are called the **zeros** of the system. The ODE is said to be a minimal realization if the numerator and denominator of the associated transfer function have no common roots, i.e. there are no common poles and zeros. For minimal systems, $|P(z)| \mid=\infty$ for any pole $p$ and $|P(z)|=0$ for any zero $z \in \mathbb{C}$.

---
$\star$ These notes will focus on continuous-time dynamical systems but there are analogues of most results for discrete-time systems.
$\dagger$ The derivatives for a signal $f: \mathbb{R}_{\geq 0} \rightarrow \mathbb{R}$ are denoted by $f^{[k]}:=\frac{d^k}{d t^k} f$ for $k=1,2, \ldots$ Alternatively they are denoted by $\dot{f}:=\frac{d}{d t} f, \ddot{f}:=\frac{d^2}{d t^2} f$, etc.





