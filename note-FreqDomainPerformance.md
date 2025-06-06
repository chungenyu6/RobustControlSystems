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

The competing design objectives can be specified using various input/output signals of the feedback system. In particular, the controller $C$ should be designed to satisfy the following:

- Stability: At a minimum, the feedback system should be stable as in Definition 3. Theorem 3 can be used to check for stability of the feedback system. Specifically, $P(s)$ and $C(s)$ should have no RHP pole/zero cancellations and $S(s)$ should be stable.
  
- Reference Tracking: The controller should be designed so that the system output $y$ tracks, i.e. closely follows, the reference command $r$. In the absence of noise the tracking error is given by $e=r-y$ and thus $E(s)=S(s) R(s)$ (Equation 6). If the reference command is $r(t)=A \cos (\omega t)$ then the steady-state tracking error satisfies:
$$
e(t) \rightarrow A|S(j \omega)| \cos (\omega t+\angle S(j \omega))
$$
> For example, if $|S(j \omega)|=0.05$ then the error amplitude is only $5 \%$ of the reference amplitude at the frequency $\omega$. Thus good tracking at frequency $\omega$ requires $|S(j \omega)| \ll 1$.

- Disturbance Rejection: The controller should be designed so that a disturbance $d$ has small effect on the output $y$. These signals are related by $Y(s)=P(s) S(s) D(s)$ (Equation 6). Thus rejection of a sinusoidal disturbance $d(t)=A \cos (\omega t)$ requires $|P(j \omega) S(j \omega)|$ to be "small". One notion of "small" is that the controller should reduce the effect of the disturbance as compared to the performance with no control. In particular, if there is no control, i.e. $C(s)=0$, then the disturbance and output are related by $Y(s)=P(s) D(s)$. Thus the controller reduces the effect of a disturbance if $|P(j \omega) S(j \omega)| \ll|P(j \omega)|$. In other words, $|S(j \omega)| \ll 1$ implies good disturbance rejection, i.e. that the effect of the disturbance with control is significantly less than the effect with no control.
  
- Actuator Effort: The control $u$ should remain within allowable levels. Consider the relation from reference command to control: $U(s)=C(s) S(s) R(s)$ (Equation 6). This implies that the control effort required to track a reference signal at frequency $\omega$ is determined by $|C(j \omega) S(j \omega)|$. Note that the requirement on actuator effort is not simply $|C(j \omega) S(j \omega)| \& 1$ because some control is required to perform the tracking. To clarify this statement consider the input required to track a constant reference $\bar{r}$ in steady-state. The DC (steady-state) gain of the plant $P$ is defined to be $P(0)$. Thus if $y(t) \rightarrow \bar{r}$ and $u(t) \rightarrow \bar{u}$ then $\bar{r}=P(0) \bar{u}$. In other words, tracking $\bar{r}$ in steady-state (assuming $d(t)=0$ ) requires the control $\bar{u}=\frac{1}{P(0)} \bar{r}$. As a consequence, it does not make sense to require $|C(0) S(0)|<\left|\frac{1}{P(0)}\right|$ as this would prevent steady state tracking. More generally, tracking of dynamic signals requires additional control beyond the steady-state value. As a rule of thumb, a sensible requirement on reference $r$ to control $u$ is:
$$
|C(j \omega) S(j \omega)| \leq \frac{2.5}{|P(0)|}
$$


   The factor of 2.5 allows for control beyond that required for perfect steady state tracking. Multiply Equation 9 by $|P(j \omega)|$ to rewrite the actuator requirement as:
$$
|T(j \omega)| \leq 2.5\left|\frac{P(j \omega)}{P(0)}\right|
$$


- Noise Rejection: Measurement inaccuracies, e.g. noise $n$, should have small effect on the output $y$. This input/output pair is related by $Y(s)=-T(s) N(s)$ (Equation 6). Thus good noise rejection at frequency $\omega$ requires $|T(j \omega)| \ll 1$. It is also required that the noise does not cause large control effort. The relation from noise to control is $U(s)=-C(s) S(s) N(s)$ (Equation 6). This is the same as from $r$ to $u$ (except for the negative sign). Hence Equation 10 also ensures reasonable gain from noise to control.
  
- Robustness to Model Uncertainty: The controller must be robust, i.e. insensitive, to model errors. Additional robustness metrics will be reviewed later. It will be shown that a rule of thumb for good robustness is to have $|S(j \omega)| \leq 2.5$ for all $\omega$.

Good reference tracking and disturbance rejection at a frequency $\omega$ both require $|S(j \omega)| \ll$ 1. Good noise rejection at a frequency $\omega$ requires $|T(j \omega)| \ll 1$. These requirements are in direct conflict. Specifically, recall that $S(j \omega)+T(j \omega)=1$ at all frequencies. Hence it is not possible to make both $|S(j \omega)|$ and and $|T(j \omega)|$ small at a specific frequency. This conflict is resolved by splitting the design objectives based on frequency. Typically, reference commands and disturbances dominate at low frequencies while noise dominates at high frequencies.