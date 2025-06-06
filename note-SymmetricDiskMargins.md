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

The previous section [[202304271350-SimultaneousGain&PhaseVariations]] defined a disk margin using the nominal sensitivity $S$. Specifically, the margin $0 \leq \bar{m}_S \leq 1$ implies the feedback system remains stable for gain and/or phase variations in $\alpha \in \operatorname{Disk}\left(\frac{1}{1+\bar{m}_S}, \frac{1}{1-\bar{m}_S}\right)$. As $\bar{m}_S \rightarrow 1$ uncertainty set $\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ converges to the halfplane $\left\{z: \operatorname{Re}(z)>\frac{1}{2}\right\}$. Thus the largest disk margin $\bar{m}_S$ cannot be used to prove stability respect to gain/phase perturbations with real part in the interval $(0,0.5]$. These considerations motivation the introduction of an symmetric disk margin.

Theorem 2. Assume $C$ stabilizes the nominal model $P$ and let $m \leq 1$ be given. Then $C$ stabilizes the perturbed model $\alpha P$ for all $\alpha \in \operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$ if and only if $\|S-T\|_{\infty} \leq \frac{1}{m}$.
Proof. It can be shown, via complex algebra, that the (open) Disk $\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$ is equivalent to following set of complex numbers:
$$
\operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)=\left\{\frac{1-z}{1+z}: z \in \mathbb{C} \text { with }|z|<m\right\} .
$$
The remainder of the proof is to the one given for Theorem 1. Both results follow from the more general small gain theorem to be presented later.

This result is another robust stability theorem. The largest disk is defined with $\bar{m}_{S T}:=$ $\frac{1}{\|S-T\|_{\infty}}$ and $\bar{m}_{S T}$ is called the symmetric disk margin (Barrett 1980, Dailey 1981). The term "disk margin" typically refers to this symmetric disk margin definition. Again, $\bar{m}_{S T} \leq 1$ is required to apply the theorem but this typically holds in any real feedback system. The corresponding uncertainty set is symmetric in the sense that it has diameter along the real axis interval $\left(I_L, I_R\right)$ where $I_L:=\frac{1-\bar{m}_{S T}}{1+\bar{m}_{S T}}$ and $I_R:=\frac{1}{I_L}$. The geometric mean of the interval endpoints is the nominal value, i.e. $\sqrt{I_L I_R}=1$. The interval endpoints satisfy $I_L \rightarrow 0$ and $I_R \rightarrow \infty$ as $\bar{m}_{S T} \rightarrow 1$. Thus the uncertainty set converges to the to the half-plane $\{z: \operatorname{Re}(z)>0\}$ as $\bar{m}_{S T} \rightarrow 1$. Thus the largest symmetric disk margin $\bar{m}_{S T}$ can, in principle, be used to prove stability respect to all gain/phase perturbations with positive gain.

Finally, we note that the disk margins can also be related to the classical gain and phase margins. The symmetric disk margin $\bar{m}_{S T}$ ensures the feedback system remains stable for all pure gains (no phase) in the interval $\left(I_L, I_R\right)$. Thus the system achieves classical gain margins of at least $\underline{g} \leq \frac{1}{1+m}$ and $\bar{g} \geq \frac{1}{1-m}$. Similarly, it can be shown that a symmetric disk margin $\bar{m}_{S T}$ ensures classical phase margins of at least $\bar{\theta} \geq 2 \tan ^{-1}\left(\bar{m}_{S T}\right)$. These are minimum classical margins implied by the symmetric disk margin. A reasonable rule of thumb is to require a symmetric disk margin $\bar{m}_{S T} \geq \frac{1}{3}$. This implies classical gain and phase margins of at least $[0.5,2]$, i.e. $\pm 6 \mathrm{~dB}$, and $\pm 37^{\circ}$. It is important to emphasize that the symmetric disk margin is stronger in the sense that it allows simultaneous variations within the uncertainty set $\operatorname{Disk}\left(I_L, I_R\right)$. This is equivalent to excluding the Nyquist curve from approaching -1 along any direction.
