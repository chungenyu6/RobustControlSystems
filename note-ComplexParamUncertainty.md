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

Complex uncertainty can be used to model simultaneous gain and phase variations, e.g. as in the SISO disk margins introduced previously. A simple description of complex uncertainty $\alpha \in \mathbb{C}$ is given by a disk centered at $\alpha_0 \in \mathbb{C}$ and with radius $w_\alpha>0$. As noted above, it will be useful to provide a normalized description of this uncertainty. Specifically, this complex disk is equivalent to $\alpha_0+w_\alpha \delta_\alpha$ where $\delta_\alpha \in \mathbb{C}$ is the normalized uncertainty with $\left|\delta_\alpha\right| \leq 1$. The "nominal" or best guess value for the complex parameter $\alpha$ is the disk center $\alpha_0$. Note that $\delta_\alpha=0$ corresponds to this nominal value and $\delta_\alpha=e^{j \phi}$ with $0 \leq \phi<2 \pi$ corresponds to parameters on the boundary of the complex disk.

The complex uncertainties used for disk margin analysis are slightly more complicated. Let $\operatorname{Disk}\left(I_L, I_R\right)$ denote the closed disk in the complex plane with diameter on the real axis corresponding to the interval $\left[I_L, I_R\right] . \ddagger$ The first disk margin analysis considered the distance from the Nyquist curve to -1 . This analysis corresponds to gain/phase variations in the (non-symmetric) Disk $\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ for some $m \in[0,1)$. Appendix A reviews several useful transformations for complex numbers including translations, rotations/scalings, and inversions [[202304271726-ComplexTransformations]]. These transformations can be used to provide a normalized description for the non-symmetric disk uncertainty. The following equivalence is shown in Appendix A:

$$
\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)=\left\{\alpha=\frac{1}{1-m \delta} \in \mathbb{C}: \delta \in \mathbb{C},|\delta| \leq 1\right\}
$$
The nominal value $\alpha=1$ corresponds to the normalized value $\delta=0$. Note, however, that the center of the disk is $\alpha=\frac{1}{1-m^2}$ and this is not then nominal value.

We also defined a symmetric disk margin using $\operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$ for some $m \in[0,1)$. The following equivalence is also shown in Appendix A:
$$
\operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)=\left\{\alpha=\frac{1+m \delta}{1-m \delta} \in \mathbb{C}: \delta \in \mathbb{C},|\delta| \leq 1\right\}
$$
Again the nominal value $\alpha=1$ corresponds to the normalized value $\delta=0$.
Example 2. The Matlab command ucomplex can be used to construct (scalar) complex uncertainty. The following snippet of code constructs a feedback system with a second-order plant $P$, proportional controller $C$ and complex uncertainty $\alpha$ in the symmetric disk $m=\frac{1}{3}$.

	% Plant and Controller
	P = tf(1,[1 12 20]);
	C = 15;
	
	% Create complex uncertainty (normalized and symmetric disk)
	delta = ucomplex(’delta’,0);
	m = 1/3;
	alpha = (1+m*delta)/(1-m*delta);
	
	% Closed-loop sensitivity function with symmetric disk uncertainty
	S = feedback(1,P*alpha*C);
	
	% Bode plot of closed-loop sensitivity (samples and nominal)
	[Ssamp,samples] = usample(S,20); % Generate 20 samples
	bode(Ssamp,’b-.’,S.NominalValue,’r’);

![[Pasted image 20230427165439.png|500]]

---
†This is change in notation from earlier where we considered open disks. The notation Disk $\left(I_L, I_R\right)$ is now closed and includes the boundary.