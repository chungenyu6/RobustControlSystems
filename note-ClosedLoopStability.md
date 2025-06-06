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
Related Note     : [[02-FreqDomainCtrlDesign]]


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

![[Pasted image 20230427105254.png|400]]

The primary performance requirement for the controller is that it must ensure that the feedback system is stable. There are 15 input/output pairs in Equation 6. It is possible that some of these transfer functions are stable and some are unstable. For example, this occurs if $P$ and $C$ have an (exact) pole/zero cancellation in the right-half of the complex plane (RHP). This motivates the following definition for stability of the feedback system.

Definition 3. The feedback system is defined to be stable if all possible transfer functions in the system $(r$ to $e, d$ to $u, n$ to $y$, etc.) are stable.

It is important to note that the stability of the feedback system can be different from the stability of the individual components $P$ and $C$. For example, the feedback system can be unstable even if both $P$ and $C$ are stable. Conversely, the feedback system can be stable even if $P$ and/or $C$ is unstable. An important observation is that the feedback system will be unstable (as defined above) if there is a RHP pole/zero cancellation between $P(s)$ and $C(s)$. It is emphasized that this instability occurs even if there is a perfect RHP pole/zero cancellation. Thus a controller should never be designed to cancel a RHP pole or zero in the plant as this will result in an unstable feedback system. A simple stability condition for the feedback system is now stated in terms of the transfer functions $P(s)$ and $C(s)$.

Theorem 3. Consider a feedback system where $P(s)$ and $C(s)$ have minimal realizations. Moreover, assume there are no RHP pole/zero cancellations in the product $P(s) C(s)$. Then the feedback system is stable if and only if $1+P(s) C(s)$ has no RHP zeros. Equivalently, the feedback system is stable if and only if the sensitivity $S(s)$ is stable.
