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


This section illustrates the basic $S(s)$ and $T(s)$ tradeoffs using the following simple example:
Plant: $\dot{y}(t)=u(t) \quad$ Control: $u(t)=K_p e(t)$
The plant is a single integrator with transfer function $P(s)=\frac{1}{s}$. The controller is a proportional gain, $C(s)=K_p$. The sensitivity and complementary sensitivity for this example are:
$$
S(s)=\frac{1}{1+P(s) C(s)}=\frac{s}{s+K_p} \quad \text { and } \quad T(s)=\frac{P(s) C(s)}{1+P(s) C(s)}=\frac{K_p}{s+K_p}
$$
The left side of Figure 3 shows the Bode magnitude plot for $S(s)$ and $T(s)$ with $K_p=1$. The plot also shows the loop transfer function $L(s)=P(s) C(s)$. There are three frequency regions of importance:

- Low Frequencies: In this region, the loop gain is large $|L(j \omega)| \gg 1$ and, as a result, $|S(j \omega)| \ll 1$. The small sensitivity corresponds to good reference tracking and disturbance rejection at low frequencies. Another consequence of the large loop gain is that $|T(j \omega)| \approx 1$. This implies that noise appears in the output with little attenuation, i.e. there is poor noise rejection at low frequencies. The poor noise rejection is a consequence of the good reference tracking and disturbance rejection obtained by relying on the feedback measurement at low frequencies.

- High Frequencies: In this region, the loop gain is small $|L(j \omega)| \ll 1$ and, as a result $|T(j \omega)| \ll 1$. The small complementary sensitivity corresponds to good noise rejection at high frequencies. Another consequence of the small loop gain is that $|S(j \omega)| \approx 1$. This implies that both the reference tracking and disturbance rejection are poor in this frequency range. The poor tracking and disturbance rejection are a consequence of the good noise rejection obtained by having small feedback at high frequencies.

- Middle Frequencies: The loop transfer function for this simple example has unity gain, i.e. $\left|L\left(j \omega_c\right)\right|=1=0 d B$, at a single frequency $\omega_c=K_p=1 \frac{r a d}{s e c}$. This frequency defines the (loop) bandwidth which is a measure of the system speed of response. Note that the closed-loop (see Equation 12) has a single pole $s_1=-1 \frac{\text { rad }}{s e c}$ at this same frequency. This corresponds to a time constant of $\tau_1=1 \mathrm{sec}$. More precise definitions of bandwidth are given below. It will be shown later that the characteristics of the middle frequency region impact the stability and robustness of the closed loop.

![[Pasted image 20230427112811.png | 500]]

The right plot of Figure 3 shows the output response $y(t)$ (red dashed) due to both a reference $r(t)$ (blue solid) and noise $n(t)$ input. The reference $r(t)$ and noise $n(t)$ inputs correspond to "low" and "high" frequency signals. For $K_p=1$ the system bandwidth, as defined above, is $\omega_c=1 \frac{\mathrm{rad}}{\mathrm{sec}}$. This is sufficiently low that most of the noise is rejected and the output $y(t)$ is fairly smooth. However, the output has a noticeable lag relative to the reference signal. This is because the reference signal has frequency content in the $1-3 \frac{\mathrm{rad}}{\mathrm{sec}}$ range which is above the system bandwidth.

Increasing the proportional gain to $K_P=10$ yields the results shown in Figure 4 . The left plot again shows the Bode magnitude plots for $S(s), T(s)$, and $L(s)$. The larger gain pushes the system bandwidth to $10 \frac{\mathrm{rad}}{\text { sec }}$. For this gain the closed-loop (see Equation 12) pole is at $s_1=-K_p=-10 \frac{\mathrm{rad}}{\text { sec }}$ with corresponding time constant $\tau_1=0.1$ sec. Thus larger bandwidths correspond to a faster speed of response. The good tracking and disturbance rejection extends over a wider "low" frequency region. The disadvantage is that the complementary sensitivity function has larger gain at high frequencies. This corresponds to degraded noise rejection. The right plot of Figure 4 shows the time domain response due to reference and noise inputs. The output responds faster to the reference command but is also degraded due to the noise. Both of these features support the conclusions from the frequency domain plots (better reference tracking but degraded noise rejection).

![[Pasted image 20230427112914.png | 500]]

One final aspect for discussion is the speed of response. The step response settling time can be used to measure the speed of a simple system. An alternative, frequency domain measure for the speed of response is the "bandwidth". There are three distinct methods to measure the bandwidth. First, a loop crossover frequency $\omega_c$ is defined by $\left|L\left(j \omega_c\right)\right|=1=$ $0 d B$. Typically there is only a single loop crossover frequency but in some cases there can be more than one. The loop bandwidth is given by the lowest loop crossover frequency. $\mathrm{A}$ higher bandwidth corresponds to a faster speed of response. A second measure of speed is the sensitivity bandwidth, denoted $\omega_S$. This is defined as the highest frequency such that $|S(j \omega)| \leq$ $\frac{1}{\sqrt{2}}=-3 d B$ for all $\omega \leq \omega_S$. This is roughly a measure of the frequency range for tracking and disturbance rejection. The third and final measure of speed is the complementary sensitivity bandwidth, denoted $\omega_T$. This is defined as the lowest frequency such that $|T(j \omega)| \leq \frac{1}{\sqrt{2}}=-3 d B$ for all $\omega \geq \omega_T$. This is roughly a measure of the frequency range for noise rejection.

These three different bandwidths are typically ordered by $\omega_S \leq \omega_c \leq \omega_T$. They are all labeled in Figure 5 for the plant $P(s)=\frac{1}{s^2+0.7 s+0.01}$ and controller $C(s)=1$. Note that both $|S(j \omega)|>1$ and $|T(j \omega)|>1$ for a frequency range near $\omega_c$. This implies that, for these frequencies, the system has poor noise rejection and poor reference tracking / disturbance rejection. Thus it is typically undesirable to have a large spread between $\omega_S$ and $\omega_T$.

![[Pasted image 20230427113045.png | 500]]


---

"The loop bandwidth and loop crossover frequency are the same for systems with only one loop crossover. This is the typical case.

