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
Related Note     : [[02-UncertaintyModeling]], [[202304271705-LFTInterconnections]]


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

![[Pasted image 20230427171326.png|400]]

Consider an LFT $F_U(L, \Delta)$ and partition $L=\left[\begin{array}{cc}L_{11} & L_{12} \\ L_{21} & L_{22}\end{array}\right]$. This LFT defines a matrix/system mapping input $u$ to output $e$ by the following equations:
$$
\begin{aligned}
{\left[\begin{array}{l}
v \\
e
\end{array}\right] } & =\left[\begin{array}{ll}
L_{11} & L_{12} \\
L_{21} & L_{22}
\end{array}\right]\left[\begin{array}{l}
w \\
u
\end{array}\right] \\
w & =\Delta v
\end{aligned}
$$
The negative feedback configuration shown in Figure 6 imposes the additional constraint that $u=d-e$. The second row of Equation 15 gives $e=L_{21} w+L_{22} u$. If $I+L_{22}$ is nonsingular, then these two equations can be solved for $u$ :
$$
u=\left(I+L_{22}\right)^{-1}\left(-L_{21} w+d\right)
$$
Substitute this result into Equation 20 to obtain an $\operatorname{LFT} F_u(M, \Delta)$ for the negative feedback connection with:
$$
\begin{aligned}
{\left[\begin{array}{l}
v \\
e
\end{array}\right] } & =\underbrace{\left[\begin{array}{cc}
L_{11}-L_{12}\left(I+L_{22}\right)^{-1} L_{21} & L_{12}\left(I+L_{22}\right)^{-1} \\
\left(I+L_{22}\right)^{-1} L_{21} & L_{22}\left(I+L_{22}\right)^{-1}
\end{array}\right]}_{:=M}\left[\begin{array}{l}
w \\
d
\end{array}\right] \\
w & =\Delta v
\end{aligned}
$$
Similar results can be derived for other feedback connections, e.g. positive feedback and/or with lower LFTs. There is one technical point regarding this feedback connection. The initial LFT $F_U(L, \Delta)$ is well-posed if $I-L_{11} \Delta$ is nonsingular. Nonsingularity of $I+L_{22}$ implies that we can define $M$ as in Equation 18. However, well-posedness of $F_U(M, \Delta)$ requires the additional condition that $I-M_{11} \Delta$ is nonsingular.

---
## Ex. Feedback System with Uncertainty

![[Pasted image 20230427171706.png|500]]

Consider the simple feedback system shown on the left of Figure 7. The plant is $P(s)=\frac{b}{s-a}$ where $a \in[0.8,1.1]$ and $b \in[1.7,2.6]$. The actuator dynamics are $A(s)=\frac{10}{s+10}\left(1+0.1 \Delta_A(s)\right)$ where $\Delta_A$ is stable with $\|$ Delta $_A \|_{\infty} \leq 1$. The controller is a PI law with $C(s)=\frac{3 s+4.5}{s}$. The closed-loop sensitivity from reference to error is $S(s)=\frac{1}{1+P(s) A(s) C(s)}$. The uncertainties consist of the real parameter variations in the plant and the dynamic LTI uncertainty in the actuator. This uncertainty sensitivity can be represented as a single LFT $F_U(M(s), \Delta(s))$ where $\Delta(s)$ is structured:
$$
\Delta(s)=\left[\begin{array}{ccc}
\delta_a & 0 & 0 \\
0 & \delta_b & 0 \\
0 & 0 & \Delta_A(s)
\end{array}\right]
$$
Here $\delta_a, \delta_b \in[-1,1]$ are the normalized parametric uncertainties.
Below is a snippet of Matlab code to construct this feedback system with both parametric
and dynamic, LTI uncertainty.

	% Unstable plant with parametric uncertainty
	a = ureal(’a’,1, ’Range’, [0.8 1.1]);
	b = ureal(’b’,2, ’Range’, [1.7 2.6]);
	P = tf(b, [1 -a]);
	
	% Actuator with dynamic uncertainty
	nomAct = tf(10, [1 10]);
	DeltaA = ultidyn(’DeltaA’,[1 1]);
	A = nomAct*(1 + 0.1*DeltaA);
	
	% PI Control
	C = tf([3 4.5],[1 0]);
	
	% Uncertain closed-loop (r->e)
	S = feedback(1,P*A*C);
	
	% Extract M-Delta representation
	[M,Delta] = lftdata(S);