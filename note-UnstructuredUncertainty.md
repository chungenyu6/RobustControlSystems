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
Related Note     : [[02-MIMORobustness]], [[02-UncertaintyModeling]]


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

Return to the MIMO feedback system in Figure 5 with an $n_y \times n_u$ plant $P$. A complex matrix perturbation $\alpha \in \mathbb{C}^{n_u \times n_u}$ is introduced at the plant input. The nominal value for this perturbation is $\alpha=I_{n_u}$. Deviations of $\alpha$ away from this nominal value introduces simultaneously perturbations to all channels. Moreover, this introduces cross-coupled uncertainty, i.e. the perturbation allows the command from output $i$ of the controller to feed into the input $j$ of the plant. There are several ways to define a stability margin using this type of unstructured uncertainty. As one example, let the perturbation have the form $\alpha:=I_{n_u}+\Delta$ where $\Delta \in \mathbb{C}^{n_u \times n_u}$ represents the perturbation away from nominal. The stability margin, for this class of perturbations, is defined to be the largest $m \in[0,1]$ such that the feedback loop is stable for all $\bar{\sigma}(\Delta)<m$. The next theorem provides a necessary and sufficient condition for robust stability with respect to this class of uncertainty.

![[Pasted image 20230427152552.png|500]]

Theorem 2. Assume $C$ stabilizes the nominal model $P$ and let $m \leq 1$ be given. Then $C$ stabilizes the perturbed model $P\left(I_{n_u}+\Delta\right)$ for all $\bar{\sigma}(\Delta)<m$ if and only if $\left\|T_I\right\|_{\infty} \leq \frac{1}{m}$.

Proof. A sketch of the proof is given here. The feedback system shown in Figure 5 can be manipulated into the general $M-\Delta$ loop (Figure 4) with $M:=-T_I$. The theorem then follows from the small gain theorem (Theorem 1). There are a few additional technical details, e.g. it must be shown that stability of the $M-\Delta$ loop is equivalent to stability of all closed-loop transfer functions in Figure 5.

The perturbed plant is $P\left(I_{n_u}+\Delta\right)$ and this is called an input multiplicative uncertainty. Other uncertainty models can be used, e.g. an output multiplicative uncertainty $\left(I_{n_y}+\Delta\right) P$ or an additive uncertainty $P+\Delta$. These alternatives will yield different robust stability conditions than the one given in Theorem 2. For SISO plants, the specific condition in Theorem 2 reduces to $\|T\|_{\infty} \leq \frac{1}{m}$ and the uncertainty corresponds to $\alpha \in \operatorname{Disk}(1-m, 1+m)$. This is a variation on the disk margins considered previously for SISO feedback systems. Specifically, this is a disk margin based on $T$.

Example 2. Consider the spinning satellite example in the previous section. This $2 \times 2$ feedback system has $\left\|T_I\right\|_{\infty}=10.05$. Hence it can only tolerate input multiplicative perturbations up to size $\bar{\sigma}(\Delta)<0.0995$. This small margin to unstructured uncertainty confirms the sensitivity to coupled, simultaneous uncertainties as observed in the previous section.
