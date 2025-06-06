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
Related Note     : [[02-StbltyMargins&Rbstness]]


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

This section will discuss another type of safety factor called the phase margin. The phase margin is the amount of allowable variation in the phase of the plant before the closed-loop becomes unstable. To make this concrete, consider the feedback diagram shown in Figure 8 . Again, $P(s)$ is the "nominal" model used to design the controller $C(s)$. The complex number $e^{-j \theta}$ is introduced to represent phase variations in the plant dynamics. The loop transfer function, including this phase variation, is given by $L_\theta(s)=e^{-j \theta} P(s) C(s)$. Note that the nominal loop transfer function corresponds to $\theta=0$ and this is denoted as $L(s)=P(s) C(s)$. The term phase variation arises because $\angle L_\theta(j \omega)=\angle L(j \omega)-\theta$, i.e. $\theta$ modifies the angle (phase) of the dynamics. Phase variations can occur due to time delays in the feedback loop, e.g. due to implementations on embedded processors, or simply due to deviations in the plant dynamics. Sufficient phase margin is required to ensure that such delays and model variations do not destabilize the system.

![[Pasted image 20230427114526.png | 400]]

Assume that the controller has been designed to stabilize the nominal design model $P(s)$, i.e. the closed-loop system is stable for $\theta=0$. The phase variations will cause the closedloop poles to move continuously in the complex plane. It is possible for the closed-loop poles to move into the RHP (unstable closed loop) if the phase $\theta$ is increased or decreased by a sufficiently large amount. The critical phases are values for which the closed-loop poles are on the imaginary axis. These phases mark the transition as poles move from the LHP (stable) into the RHP (unstable). In particular, a critical phase $\theta_0$ causes the closed-loop to have a pole on the imaginary axis $s=j \omega_0$ for some frequency $\omega_0 \geq 0$. Thus the sensitivity $S_{\theta_0}(s)=\frac{1}{1+e^{-j \theta_0 L(s)}}$ has a pole $s=j \omega_0$ which is equivalent to $1+e^{-j \theta_0} L\left(j \omega_0\right)=0$ (Theorem 3). To summarize, a phase variation $\theta_0$ causes a closed-loop pole at $s=j \omega_0$ if and only if $e^{-j \theta_0} L\left(j \omega_0\right)=-1$.

Two additional facts are required before stating the formal phase margin definition. First, complex numbers repeat with every $360 \mathrm{deg}(=2 \pi)$ change in phase, i.e. $e^{j \theta}=e^{j \theta+2 \pi}$. Thus only phases in the range $-180 \mathrm{deg} \leq \theta \leq 180 \mathrm{deg}$ need to be considered. Second, positive and negative phase variations have a similar effect. Specifically, the complex conjugate of a transfer function $L(j \omega)$ is $L(-j \omega)$. Therefore the complex conjugate of $e^{-j \theta_0} L\left(j \omega_0\right)=-1$ is $e^{j \theta_0} L\left(-j \omega_0\right)=-1$. Thus $\theta_0$ is a critical phase causing a closed loop pole at $s=j \omega_0$ if and only if $-\theta_0$ is a critical phase causing a closed-loop pole at $s=-j \omega_0$. Either sign of critical phase will cause instability. Based on these facts, the phase margin specifies the maximum variation for which the closed-loop remains stable as defined below.

Definition 5 (Phase Margin). The phase margin consists of an upper limit $\bar{\theta} \geq 0$ such that:
1. the closed-loop is stable for all phase variations $\theta$ in the range $-\bar{\theta}<\theta<\bar{\theta}$, and
2. the closed-loop is unstable for $\theta=\bar{\theta}$ (if $\bar{\theta}<\infty$ ).

The phase margin $\bar{\theta}$ corresponds to the variation that lies at the boundary between stable and unstable closed-loops. In some cases the closed-loop remains stable for all phases in the range $0 \leq \theta \leq 180 \mathrm{deg}$. In this case, the upper limit is defined to be $\bar{\theta}=+\infty$. As a rule of thumb, the phase margin limit should satisfy $\bar{\theta}>45 \mathrm{deg}$ for good robustness to model uncertainty. This is frequently stated as $\pm 45 \mathrm{deg}$ of required phase margin for good robustness. This rule of thumb is a good starting point but requirements may differ slightly depending on the specific problem.

The condition for critical phases can be used to calculate the phase margin directly from the Bode plot of $L(s)$. Specifically, the condition $e^{-j \theta_0} L\left(j \omega_0\right)=-1$ for some phase $\theta_0$ implies that $\left|L\left(j \omega_0\right)\right|=1=0 d B$. The phase margins are computed from a Bode plot as follows:
1. Identify the frequencies $\left\{\omega_1, \ldots, \omega_N\right\}$ where $\left|L\left(j \omega_0\right)\right|=1=0 d B$. These are called the gain crossing frequencies or phase margin frequencies. There may be zero, one, or many phase margin frequencies.
2. The critical phase for each frequency $\omega_i$ satisfies $-\theta_i+\angle L\left(j \omega_i\right)=-180 \operatorname{deg}$. Thus the critical phases are $\theta_i=\angle L\left(j \omega_i\right)+180 \operatorname{deg}(i=1, \ldots, N)$. To perform this calculation, first express $\angle L\left(j \omega_i\right)$ in the interval $[0,-360]$ deg by adding or subtracting factors of $360 \mathrm{deg}$. This yields a critical phase $\theta_i$ in the range $[-180,+180] \mathrm{deg}$ and results in a closed-loop pole at $s=j \omega_i$. As an example, if $\angle L\left(j \omega_i\right)=-135 d e g$ then the critical phase is $\theta_i=-135+180=45 \operatorname{deg}$.
3. The phase margin $\bar{\theta}$ is the smallest (in magnitude) critical phase, i.e. it is the smallest value of $\left|\theta_i\right|$ for $i=1, \ldots, N$.

Finally, a pure time delay $\tau_d$ has the frequency response $e^{-j \omega \tau_d}$. For a fixed frequency this introduces a phase variation $e^{-j \theta}$ with $\theta=\omega \tau_d$. Thus the time delay margin can be computed from the phase margin as follows:
1. Identify the phase margin frequencies $\left\{\omega_1, \ldots, \omega_N\right\}$ and corresponding critical phases $\left\{\theta_1, \ldots, \theta_N\right\}$ from a Bode plot.
2. The critical delays are given by $\tau_{d, i}=\left|\frac{\theta_i}{\omega_i}\right|>0$ for $i=1, \ldots, N$.
3. The time delay margin $\bar{\tau}_d$ is the smallest critical delay.