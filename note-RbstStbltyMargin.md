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
Related Note     : [[02-RobustStability]]


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

Consider an uncertain system $F_U(M, \Delta)$ with uncertainty structure $\Delta$ and modeled uncertainty $\mathbf{B}_{\boldsymbol{\Delta}}$. The notions of nominal and robust stability are defined next.

Definition 1. Consider the uncertain system $F_U(M, \Delta)$ with the modeled uncertainty defined by $\mathbf{B}_{\boldsymbol{\Delta}}$. The uncertain system is nominally stable if $M$ is stable. The uncertain system is robustly stable if it is nominally stable and $F_U(M, \Delta)$ is both well-posed and stable for all $\Delta \in \mathrm{B}_{\Delta}$

Robust stability is a binary (yes/no) property for the uncertain system, i.e. the uncertain system is either robustly stable or it is not. It will be useful to have a more quantitative measure of robustness. The robust stability margin, as defined next, provides such a measure.

Definition 2. Consider the uncertain system $F_U(M, \Delta)$ with the structured uncertainty defined by $\boldsymbol{\Delta}$. Assume the system is nominally stable. The stability margin is the largest value $m$ such that $F_U(M, \Delta)$ is both well-posed and stable for all $\Delta \in \Delta$ with $\|\Delta\|_{\infty}<m$.

The system is robustly stable if and only if it is nominally stable and has a stability margin $m>1$. Note that this stability margin is defined with respect to the normalized uncertainties. This normalization allows many (possibly) different sources of uncertainty to be considered in a single stability margin.

The Matlab function robstab computes the stability margin for an uncertain system. The numerical algorithms underlying this function will be detailed in later notes. For now it is sufficient to note that computing the exact stability margin is difficult in general. Instead, the function computes lower and upper bounds, $\underline{m}$ and $\bar{m}$, on the stability margin $m$. The lower bound provides a guaranteed stability bound, i.e. the uncertain system $F_U(M, \Delta)$ is robustly stable for all $\Delta \in \Delta$ with $\|\Delta\|_{\infty} \leq \underline{m}$. The upper bound indicates a level at which robust stability is lost. The function robstab returns a specific "worst-case" perturbation $\Delta_{w c} \in \boldsymbol{\Delta}$ that destabilizes the system and has $\|\Delta\|_{\infty}=\bar{m}$. This perturbation causes $F_U\left(M, \Delta_{w c}\right)$ to have poles on the imaginary axis at $\pm j \omega_{w c}$. The function robstab also returns this critical frequency $\omega_{w c}$ and this often provides additional insight into the cause of instability.

---
## Ex
Example 4 . Consider the LTI system $P(s)$ that depends on two uncertain real parameters $a \in[1,3]$ and $b \in[3.5,4.5]$ with nominal values $\left(a_0, b_0\right)=(2,4)$. The uncertain system is defined as $P(s)=\frac{1}{s^2+c_1 s+c_2}$ where:
$$
\begin{aligned}
& c_1:=4-(a-2)^2-4(b-4)^2 \\
& c_2:=1+(a-2)+2(b-4)+4(b-4)(a-2)
\end{aligned}
$$
This particular uncertain system was considered in the previous example. It has an LFT representation $F_U(M(s), \Delta)$ where $M(s)$ is a $7 \times 7$ stable, LTI system. Thus $F_U(M(s), \Delta)$ is nominally stable.

![[Pasted image 20230427174551.png|500]]

This system only has two real parameter uncertainties. This allows for a graphical interpretation for the stability region, robust stability, and stability margin. The left plot in Figure 5 shows the set of modeled uncertainty $(a, b) \in[1,3] \times[3.5,4.5]$ (black rectangle) and the nominal value $\left(a_0, b_0\right)=(2,4)$ (black dot). The right plot is similar but in terms of the normalized uncertainties $\left(\delta_a, \delta_b\right) \in[-1,1] \times[-1,1]$ (black rectangle) and the nominal value $\left(\delta_{b 0}, \delta_{b 0}\right)=(0,0)$ (black dot). The set of parameter values $(a, b)$ that yield a stable $P(s)$ can also be computed from the following fact: the characteristic equation $s^2+c_1 s+c_2=0$ has all roots in the LHP if and only if $c_1>0$ and $c_2>0$. This set of parameter values yielding a stable system $P(s)$ is given by the interior of the blue curve on both plots.

There are points outside the blue curve and inside the black rectangle in both plots of Figure 5. These correspond to parameter values in the modeled uncertainty (inside the black rectangle) that cause $P(s)$ to be unstable (outside the blue curve). As a particular example, $(a, b)=(2.71,3.65)$ is in the modeled uncertainty (red dot in left plot) but causes $c_2=0$, i.e. $P(s)$ is unstable. The corresponding normalized values are $\left(\delta_a, \delta_b\right)=(0.707,0.707)$ (red dot in right plot). The system $P(s)$ is not robustly stable.

The degree of robustness is quantified by the stability margin. For this system the stability margin is the largest value $m$ such that $F_U(M, \Delta)$ is stable for all $\left(\delta_a, \delta_b\right)$ in the (open) cube $(-m, m) \times(-m, m)$. The largest such hypercube is given by $m=0.707$ and is shown as the red dashed curve in the right plot. The normalized values $\left(\delta_a, \delta_b\right)=(0.707,0.707)$ (red dot) are on the boundary of this cube and cause instability. All points in the interior of this cube are in the stable region. This cube in the normalized variables corresponds to the rectangle of actual values $(a, b)=(1.29,2.71) \times(3.65,4.35)$ (red dashed rectangle on left plot).

To summarize, the system is nominally stable but is not robustly stable for the modeled uncertainty. The stability margin is $m=0.707$ with this modeled uncertainty. Thus the system can tolerate up to $70.7 \%$ of the modeled uncertainty. There is a destabilizing combination of the parameters at the boundary of $70.7 \%$ of the modeled uncertainty.

The use of normalized uncertainties allows for direct comparison of the parameters $(a, b)$. The margin is specified as a fraction of the modeled uncertainty. It must be emphasized that robust stability and the stability margin, as defined above, depend on the specific choices for the uncertainty ranges. In other words, changing the range of uncertainty will change the stability margin. For example, suppose the parameters were known to satisfy $a \in[1.5,2.5]$ and $b \in[3.75,4.25]$ with the same nominal value $\left(a_0, b_0\right)=(2,4)$. In this case the modeled uncertainty lies entirely within the stable region, i.e. the system is robustly stable. Moreover, the stability margin for this modeled uncertainty is $m=1.41$, i.e. the system can tolerate up to $141 \%$ of this modeled uncertainty.

---
Example 5. Consider a feedback system with the following plant and controller with $a=10$ :
$$
P(s):=\frac{1}{s^2+a^2}\left[\begin{array}{cc}
s-a^2 & a(s+1) \\
-a(s+1) & s-a^2
\end{array}\right] \text { and } C(s):=\left[\begin{array}{ll}
1 & 0 \\
0 & 1
\end{array}\right]
$$
This example is taken from a 1978 CDC paper by Doyle. The dynamics represent a simplified model for a spinning satellite. Additional details can be found in Section 3.7 of Skogestad and Postlethwaite or Section 9.6 of Zhou, Doyle and Glover. This example was considered in the "Intro to MIMO Robustness" notes. The system has large loop-at-a-time margins but has poor robustness to unstructured and multi-loop disk uncertainty. In particular, it was stated this $2 \times 2$ feedback system has multi-loop input margin of $m=0.0498$. Hence the feedback system can only tolerate simultaneous and independent variations in both plant inputs with $\operatorname{Disk}(0.905,1.105)$. The numerical code to generate these results is given below.

	% Plant and Proportional Controller
	a = 10;
	P = ss([0 -a^2; 1 0],[1 0; 0 -1/a],[1 -a^2; -a -a],0);
	C = ss(eye(2));
	
	% Normalized perturbations: delta1, delta2 in [-1,1]
	delta1 = ureal(’delta1’,0);
	delta2 = ureal(’delta2’,0);
	
	% Symmetric disk perturbations
	M = [1 sqrt(2); sqrt(2) 1];
	alpha1 = lft(delta1,M);
	alpha2 = lft(delta2,M);
	
	% Sensitivity of Feedback System
	S = feedback(eye(2),P*diag([alpha1, alpha2])*C);
	
	% Robust stability
	[StabMarg,WCUnc] = robstab(S)

StabMarg =
	LowerBound: 0.0498
	UpperBound: 0.0499
	CriticalFrequency: 0

WCUnc =
	delta1: 0.0499
	delta2: -0.0499

	% Verify WCUnc destabilizes the feedback system
	pole( usubs(S,WCUnc) )
-2.0100
-0.0000

The function robstab computes upper and lower bounds on the robust stability margin. These are almost identical and hence the stability margin is $m \approx 0.0498$ as noted above. The worst-case perturbation $\delta_1=0.0499$ and $\delta_2=-0.0499$ destabilizes the feedback system by placing poles at the critical frequency $s=0$. These normalized uncertainties correspond to the perturbations $\alpha_1=1.1051$ and $\alpha_2=0.9049$.

Note that Matlab has a helper function diskmargin that directly performs the calculations for multi-loop disk margins. The same results given above can be generated with the following code. ${ }^{\S}$

	[~,MLDM] = diskmargin(C*P)
	DiskMargin = MLDM.DiskMargin/2
DiskMargin = 0.0498


---
§The function diskmargin was introduced in Matlab version R0218b. It returns symmetric disk margins as a default. The symmetric disk margin returned by Matlab is defined as $2 m$ i.e. the disk margin returned by Matlab must be scaled by a factor of two to match the notation used in these notes. Also, the now obsolete function loopmargin can be used in earlier Matlab versions to compute disk margins.