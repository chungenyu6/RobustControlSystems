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
Related Note     : [[02-MIMORobustness]]


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


The previous section considered robust stability with respect to an unstructured matrix perturbation at the plant input. This uncertainty allows for cross-coupling between the various input channels. Such cross-coupled uncertainty may not necessarily occur depending on the problem being considered. The use of unstructured uncertainty in such situations will lead to overly conservative stability margins. In other words, the computed stability margin may be smaller than observed in practice if uncertainties with cross-coupling are not expected.

Multi-loop disk margins provide a middle ground between analysis with loop-at-a-time and full, unstructured perturbations. Figure illustrates the use of multi-loop disk margins for a $2 \times 2$ MIMO plant. Scalar perturbations $\alpha_1$ and $\alpha_2$ are introduced at the two input channels of the plant. The multi-loop disk margin is defined to be the largest $m \in[0,1]$ such that the feedback loop is stable for all $\alpha_1, \alpha_2 \in \operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$ for some $m \in[0,1]$. It is emphasized that the perturbations $\alpha_1$ and $\alpha_2$ are allowed to vary independently within the disk, i.e. they are not necessarily equal.

![[Pasted image 20230427152653.png|400]]

In general, multi-loop margins can be computed at the input, output, or both. Consider a plant of dimensions $n_y \times n_u$. The multi-loop input disk margin is a single number, i.e. the margin, computed by introducing perturbations at each of the $n_u$ inputs of $P$. Similarly, the multi-loop output disk margin is a single number, i.e. the margin, computed by introducing perturbations at each of the $n_y$ outputs of $P$. Finally, the multi-loop input/output disk margin is a single number, i.e. the margin, computed by introducing perturbations at each of the $n_u$ inputs and each of the $n_y$ outputs of $P$. A typical rule of thumb is to require at least $\frac{1}{3}$ of multi-loop input disk margin. This implies classical gain variations simultaneously and independently at each input of $\pm 6 \mathrm{~dB}$. This also implies classical phase variations simultaneously and independently at each input of $\pm 37^{\circ}$. These multi-loop disk margins can be computed in Matlab using diskmargin. The theoretical framework to compute these margins will be developed next.

Example 3. Consider the spinning satellite example in the previous section. This $2 \times 2$ feedback system has multi-loop input margin of $m=0.0498$. Hence the plant can only tolerate simultaneous and independent variations in both inputs with Disk $(0.905,1.105)$. These margins are similar to those indicated by the unstructured uncertainty analysis and again indicate that the feedback is sensitivity to small perturbations.


### ChatGPT
1.  Multi-loop disk margin: Pros:

-   Provides a comprehensive analysis of the overall robustness of the system.
-   Takes into account the interactions between loops.
-   Suitable for systems with multiple feedback loops.

Cons:

-   Computationally intensive and time-consuming.
-   Can be difficult to interpret the results when there are many loops.
-   Assumes that all loops are independent, which may not always be the case.

2.  Loop-at-a-time margin: Pros:

-   Allows for a more detailed analysis of individual loops.
-   Provides a better understanding of the impact of each loop on the overall system performance.
-   Easier to interpret the results.

Cons:

-   May not capture the interactions between loops.
-   Can be time-consuming when analyzing multiple loops.
-   Assumes that each loop is independent, which may not always be the case.

3.  Unstructured uncertainty: Pros:

-   Allows for a more general analysis of the system's robustness.
-   Can capture uncertainties that are not easily modeled.

Cons:

-   May not provide a complete picture of the system's robustness.
-   Can be difficult to quantify and analyze.
-   Assumes that the uncertainties are unstructured, which may not always be the case.