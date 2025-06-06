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
Related Note     : [[02-RobustStability]]


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

The next theorem is the main result for an uncertain system $F_U(M, \Delta)$ with structured uncertainty $\Delta \in \Delta$. The theorem provides an exact, necessary and sufficient condition for the robust stability margin of such systems using the structured singular value. There is one minor abuse of notation. The structured set $\Delta$ can contain real, complex, and (stable, LTI) dynamic uncertainty. However, the structured singular value was defined for structures containing only real or complex uncertainty but no dynamic uncertainty. The notation $\mu_{\Delta}$ corresponds to the structured singular value with any dynamic uncertainty blocks replaced with corresponding complex uncertainty of the same size.

Theorem 2. Consider an uncertain system $F_U(M, \Delta)$ where $\Delta$ is a stable LTI system in the structured set $\boldsymbol{\Delta}$. Assume the uncertain system is nominally stable. The uncertain system is well-posed and stable $\forall \Delta \in \boldsymbol{\Delta}$ with $\|\Delta\|_{\infty}<m$ if and only if $\max _{\omega \in \mathbb{R} \cup\{\infty\}} \mu_{\boldsymbol{\Delta}}\left(M_{11}(j \omega)\right) \leq \frac{1}{m}$.
Proof. $(\Leftarrow)$ Assume that $\max _{\omega \in \mathbb{R} \cup\{\infty\}} \mu_{\Delta}\left(M_{11}(j \omega)\right) \leq \frac{1}{m}$ and let $\Delta$ be any stable LTI with $\|\Delta\|_{\infty}<m$. It follows from Lemma 5 that $\operatorname{det}\left(I-M_{11}(j \omega) \Delta(j \omega)\right) \neq 0$ for all $\omega \in \mathbb{R} \cup\{\infty\}$. In particular, $\operatorname{det}\left(I-M_{11}(\infty) \Delta(\infty)\right) \neq 0$ and hence $F_U(M, \Delta)$ is well-posed. By Lemma 1 , $\operatorname{det}\left(I-M_{11}(j \omega) \Delta(j \omega)\right) \neq 0$ implies that $F_U(M, \Delta)$ has no poles on the imaginary axis. Thus $F_U(M, \Delta)$ is both well-posed and has no imaginary axis poles for all $\|\Delta\|_{\infty}<m$. The remainder of the proof follows from a homotopy argument identical to the one given for unstructured uncertainty (proof of Theorem 1).

$(\Rightarrow)$ This direction is shown by contradiction. Assume $\max _{\omega \in \mathbb{R} \cup\{\infty\}} \mu_{\Delta}\left(M_{11}(j \omega)\right)>\frac{1}{m}$. Hence there is a finite frequency $\omega_0>0$ such that $\max _{\omega \in \mathbb{R} \cup\{\infty\}} \mu_{\Delta}\left(M_{11}\left(j \omega_0\right)\right)>\frac{1}{m}$. By definition of $\mu_{\Delta}$,there exists $\Delta_0 \in \mathbb{C}^{n_w \times n_v}$ with $\bar{\sigma}\left(\Delta_0\right)<m$ and $\operatorname{det}\left(I-M_{11}\left(j \omega_0\right) \Delta_0\right)=0 .{ }^{\S}$ Let $\Delta$ be the dynamic uncertainty obtained by interpolating each block of the complex uncertainty $\Delta_0$. The repeated complex scalar uncertainties can be interpolated with a SISO LTI system using Lemma 4. The complex matrix blocks can be constructed as rank one matrices (See Remark 11.1 of Zhou, Doyle, Glover for details). Hence these blocks can be interpolated with a MIMO LTI system using Lemma 4. It is possible that the uncertain system $F_U(M, \Delta)$ is not well-posed. However, if $F_U(M, \Delta)$ is well-posed then $\operatorname{det}\left(I-M_{11}\left(j \omega_0\right) \Delta\left(j \omega_0\right)\right)=0$ implies that it has a pole at $j \omega_0$ by Lemma 1 . Thus for some $\Delta$ with $\|\Delta\|_{\infty}<m$ the uncertain system $F_U(M, \Delta)$ is either not well-posed or is unstable.

---
${ }^{\S}$ There is a minor technical issue. If the uncertainty structure contains only real parameters, i.e. $\boldsymbol{\Delta} \subseteq$ $\mathbb{R}^{n_w \times n_v}$, then $\mu_{\boldsymbol{\Delta}}(M)$ can be a discontinuous function of $M$ (see paper by Pandey and Packard). In particular $\mu_{\Delta}\left(M_{11}(j \omega)\right)$ is not necessarily a continuous function of frequency. As a consequence, if the peak value of $\mu_{\Delta}\left(M_{11}(j \omega)\right)$ occurs at $\omega=0$ or $\infty$ then it may not be possible to perturb to a finite, non-zero frequency. However, interpolation is not required for pure real uncertainty structures, i.e. simply select the constant system $\Delta(s)=\Delta_0$.
