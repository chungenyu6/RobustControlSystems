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
Related Note     : [[02-HinfOptmlCtrl]]


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

![[Pasted image 20230427185313.png|400]]

The $H_{\infty}$ optimal control problem is formulated using a generic feedback architecture shown in Figure 1. This is a feedback connection (lower LFT) of a generalized plant $G$ and controller $K$. The plant and controller are both assumed to be linear and time-invariant. The plant is "generalized" in the sense that it contains the models of the actual system to be controlled as well as weights that described the performance objectives. This will be further clarified below.

The various signals in the diagram are:
- Measurements, $y$ : This is an $n_y \times 1$ signal containing all measurements available to the controller. For a classical single degree of freedom feedback system, this signal would simply be the tracking error. For a classical two degree of freedom feedback system, the controller has access to both the reference and a measurement of the plant output. In this case $y$ is a vector containing both these signals.
- Control inputs, $u$ : This is an $n_u \times 1$ signal containing all control inputs. This is simply the vector of actuator commands.
- Generalized disturbances, $d$ : This is an $n_d \times 1$ signal containing all external influences. The generalized disturbance contains any external signal that impacts the feedback system. This includes reference commands and sensor noises in addition to actual plant disturbances.
- Generalized errors, $e$ : This is an $n_e \times 1$ signal containing all regulated variables. The generalized errors contain any signal whose amplitude the controller should attempt to minimize. This contains control commands (and possibly other signals) in addition to actual reference tracking errors.
$H_{\infty}$ optimal control is a design method to synthesize a controller $K$ that: (i) stabilizes the closed-loop and, (ii) minimizes the closed-loop $H_{\infty}$ norm from $d$ to $e$. As noted above, the controller is assumed to be LTI although the controller state dimension is not specified a priori. The $H_{\infty}$ optimal control problem can be expressed as:
$$
\gamma^*:=\min _{K \text { stabilizing }} \left\|F_L(G, K)\right\|_{\infty}
$$
There are a few technical points regarding this formulation. First, there need not be a unique solution to this problem. Second, the the optimal controller can be non-proper and this leads to implementation issues, e.g. amplification of high frequency noise. Third, the conditions to construct an optimal controller are involved and efficient, numerically reliable algorithms do not exist for general MIMO problems. As a consequence, the focus will be on the related $H_{\infty}$ (sub-optimal) control problem:
$\mathbf{H}_{\infty}$ (sub-optimal) control: Given $\gamma>0$, find an LTI controller $K$ that stabilizes $F_L(G, K)$ and achieves $\left\|F_L(G, K)\right\|_{\infty}<\gamma$ or determine that no such controller exists.
Many control design problems can be formulated within this framework. 

---
## Ex
![[Pasted image 20230427185532.png|400]]
Example 1. The single DOF mixed synthesis problem presented earlier was formulated using the block diagram shown in Figure 2. The objective is to find a controller $K$ that stabilizes the closed-loop and minimizes the $H_{\infty}$ norm from $r$ to the weighted error $\tilde{e}$ and weighted control $\tilde{u}$. This is a special instance of the general $H_{\infty}$ control problem with: (i) measurement $y$ given by the tracking error, (ii) control $u$ given by the plant input, (iii) generalized disturbance equal to the reference, and (iv) generalized error given by $\left[\begin{array}{l}\tilde{e} \\ \tilde{u}\end{array}\right]$. Note that the generalized plant $G$ contains the actual plant dynamics $P$. It also contains the weights $W_S$ and $W_K$ that are used to specify the (frequency-domain) performance objectives.


