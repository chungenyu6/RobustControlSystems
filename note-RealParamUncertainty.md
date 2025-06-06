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
Related Note     : [[02-UncertaintyModeling]]


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

Consider a real parameter $p \in \mathbb{R}$ assumed to lie within the interval $[\underline{p}, \bar{p}]$. Define the center and radius of the uncertain interval as follows:
$$
p_0:=\frac{1}{2}(\bar{p}+\underline{p}) \text { and } w_p:=\frac{1}{2}(\bar{p}-\underline{p})
$$
It will be useful to provide a normalized description of this uncertainty. Specifically, the parameter interval is equivalent to $p_0+w_p \delta_p$ where $\delta_p \in[-1,1]$ is the normalized uncertainty. The "nominal" or best guess value for the parameter is assumed, for simplicity, to be at the interval center $p_0 \cdot{ }^{\dagger}$ Note that $\delta_p=0$ corresponds to this nominal value and $\delta_p= \pm 1$ correspond to the endpoints of the uncertainty interval.

Uncertain models can be constructed with one or more uncertain real parameters. An example is given below. One analysis approach is to treat an uncertain parameter as a random variable with some probability density function. A joint probability density function can be used to model correlations between multiple parameters. This approach will not be pursued here. Instead, an alternative "worst-case" analysis approach will be developed in subsequent lectures. Specifically, the uncertainty interval represents a range of equally likely parameter values. Systems with multiple uncertain parameters will be modeled with a hyperrectangle of parameter values. For example, consider a system that depends on uncertain parameters $g \in[\underline{g}, \bar{g}]$ and $\tau \in[\underline{\tau}, \bar{\tau}]$. The parameter vector $\left[\frac{g}{\tau}\right]$ is equally likely within the hyperrectangle $[\underline{g}, \bar{g}] \times[\underline{\tau}, \bar{\tau}]$. We will derive conditions which verify robustness (stability and/or performance) with respect to any value within this hyperrectangle. This approach ensures robustness even if the actual parameter values are the worst-case values within the hyperrectangle.

![[Pasted image 20230427165243.png|500]]

Example 1. Consider an LTI system $P(s)=\frac{g}{\tau s+1}$ with uncertain DC gain $g \in[2,4]$ and time constant $\tau \in[0.5,1.5] \mathrm{sec}$. The nominal parameter values are $g_0=3$ and $\tau_0=1 \mathrm{sec}$. The left side of Figure 1 shows the two-dimensional space of uncertain parameter values. This corresponds to the shaded rectangle $[2,4] \times[0.5,1.5]$. The figure also shows the nominal value (red dot) along with 20 samples (blue) chosen uniformly in the rectangle. The right side of the figure shows the Bode plot for the nominal (red) and sampled (blue) parameter values. The sampled Bode plots show the variation in the DC gain and time constant as modeled by the uncertain parameters. Systems with uncertain real parameters can be constructed in Matlab using the function ureal. The Matlab code below constructs the system $P$, generates 20 samples uniformly in the hyperrectangle, and creates a Bode plot.

	g = ureal(’g’,3,’Range’,[2 4]);            % DC Gain
	tau = ureal(’tau’,1.0,’Range’,[0.5, 1.5]); % Time Constant
	P = tf(g,[tau 1]);	
	[Psamp,samples] = usample(P,20);           % Generate 20 samples
	bode(Psamp,’b-.’,P.NominalValue,’r’);

---
†Off-centered nominal values can be considered if needed as discussed later.
