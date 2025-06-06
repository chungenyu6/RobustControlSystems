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
Related Note     : [[02-MixedSensitivitySynthesis]]


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

![[Pasted image 20230427182256.png|400]]

Consider the classical, single degree-of-freedom feedback system shown in Figure 1 . The objective is to design a controller $C$ to: (i) stabilize the plant $P$, (ii) track reference commands $r$, and (iii) use reasonable control effort $u$. In addition, the controller should provide good stability margins.

These competing design objectives can be specified using frequency domain bounds. To make this concrete, first consider a requirement on the closed-loop sensitivity specified in terms of a magnitude bound: $|S(j \omega)| \leq\left|B_S(j \omega)\right|$ for all $\omega$. The numerical control algorithms described later will require the bound $B_S$ to be specified as a transfer function or state-space system. A typical first-order performance bound has the form:
$$
B_S(s)=\frac{M_S s+A_S \omega_S}{s+\omega_{S}} 
\qquad\qquad ...... \qquad\qquad(1)
$$
The performance bound is specified by the parameters $A_S, M_S, \omega_S>0$. The DC gain for this bound is $B_S(0)=A_S$. The choice of $A_S$ specifies a requirement on the steady-state error for step reference commands: if $r(t)=r_0>0$ then the steady-state tracking error satisfies $\left|e_{s s}\right|=\left|S(0) r_0\right| \leq A_S r_0$. The high frequency gain for the performance bound is $B_S(j \infty)=M_S$. This requires the peak of the sensitivity to be no more than $M_S$ which can be related to a stability margin. Specifically, recall that the closed loop remains stable for all perturbed plants $\alpha P$ with $\alpha$ in the open $\operatorname{Disk}\left(\frac{M_S}{M_S+1}, \frac{M_S}{M_S-1}\right)$ if and only if $\|S\|_{\infty} \leq M_S$. Finally, $B_S(s)$ has a pole at $\omega_S$ and zero at $\frac{A_S \omega_S}{M_S}$. Typical parameter choices are $A_S \ll 1$ and $M_S \approx 2$. In this case, $\left|B_S\left(\omega_S\right)\right| \approx 1$ so that $\omega_S$ is approximately the sensitivity bandwidth.

A requirement on the control effort can be specified by a bound on the closed-loop transfer function from $r$ to $u$ : $|C(j \omega) S(j \omega)| \leq\left|B_C(j \omega)\right|$ for all $\omega$. An initial control bound can be determined based on actuator saturation limits of the form $|u(t)| \leq u_{\max }$. If the reference signal is a sinusoid $r(t)=r_0 \sin (\omega t)$ then the steady-state control signal is:
$$
u(t) \rightarrow|C(j \omega) S(j \omega)| r_0 \sin (\omega t+\angle C(j \omega) S(j \omega))
$$
A constant bound $B_C:=\frac{u_{\max }}{r_0}$ ensures that the steady-state control commands are within the allowable saturation limits. This bound provides a useful starting point for designs. It is obtained simply from the saturation limit $u_{\max }$ and an (approximate) reference amplitude $r_0$.
It is often important to also limit the high frequency control effort, i.e. $\left|B_C(j \omega)\right|$ should decrease at higher frequencies. This can be achieved with a control effort bound of the form:
$$
B_C(s)=\frac{M_C s+A_C \omega_C}{s+\omega_C}
\qquad\qquad ...... \qquad\qquad(3)
$$
Here $A_C:=\frac{u_{\max }}{r_0}$ corresponds to the low-frequency saturation requirement. If $M_C=0$ then this bound rolls-off above the corner frequency $\omega_C$. This corner frequency can be chosen slightly above the actuator bandwidth, e.g. $\omega_C \approx 4 \times$ the actuator bandwidth.

A more precise choice for $\omega_C$ can be determined if the actuator has a rate limit of the form: $|\dot{u}(t)| \leq \dot{u}_{\max }$. If the reference signal is a sinusoid $r(t)=r_0 \sin (\omega t)$ then the steady-state control signal is given in Equation 2. The corresponding rate is:
$$
\dot{u}(t) \rightarrow|C(j \omega) S(j \omega)| r_0 \omega \cos (\omega t+\angle C(j \omega) S(j \omega))
$$
The following bound on $|C S|$ ensures that the steady-state control commands are within the allowable saturation and rate limits:
$$
|C(j \omega) S(j \omega)| \leq \min \left(\frac{u_{\max }}{r_0}, \frac{\dot{u}_{\max }}{r_0 \omega}\right)
$$
This bound can be written as $\min \left(A_C, \frac{A_C \omega_C}{\omega}\right)$ where $A_C:=\frac{u_{\max }}{r_0}$ and $\omega_C=\frac{\dot{u}_{\max }}{u_{\max }}$. This corresponds to the saturation limit $A_C$ at low frequencies $\left(\omega \leq \stackrel{\omega}{C}^{r_0}\right)$ and the high frequency roll-off $\frac{A_C \omega_C}{\omega}$ due to the rate limit. This is well-approximated by the first-order system $B_C(s)$ in Equation 3 with $M_C=0$.

![[Pasted image 20230427182423.png|500]]

Figure 2 shows typical bounds on $S$ (left) and $C S$ (right) along with an example plant $P=\frac{1}{s+2}$ and controller $C=\frac{40}{s^2+10 s}$. The sensitivity bound $B_S$ is defined with $A_S=0.01$, $M_S=2$, and $\omega_S=1 \mathrm{rad} / \mathrm{sec}$. The choice $A_S=0.01$ represents a $1 \%$ steady-state error. These choices for $A_S$ and $M_S$ would be typical in many problems. The choice for $\omega_S$ is problem dependent and would be selected based on the desired speed of response. The control effort bound $B_C$ is defined with $A_C=5, M_C=0.005$ and $\omega_C=2 \mathrm{rad} / \mathrm{sec}$. This corresponds to actuator saturation and rate limits of $u_{\max }=5$ and $\dot{u}_{\max }=10$ with unity reference amplitudes $r_0=1$. The numerical algorithms described below will require $M_C>0$. Thus $M_C$ should be chosen as a small constant. Here it is chosen as $M_C=0.001 A_C=0.005$.
