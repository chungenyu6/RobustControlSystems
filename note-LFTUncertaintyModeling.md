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

![[Pasted image 20230427165942.png|400]]

Linear Fractional Transformations (LFTs) are a flexible tool for building more complex uncertain models from the basic atoms introduced previously. An LFT models a feedback connection of two systems or matrices. Figure 4 shows two specific LFTs. The left figure shows an LFT with $\Delta_1 \in \mathbb{C}^{n_w \times n_v}$ in feedback around the upper channels of $M \in \mathbb{C}^{\left(n_v+n_e\right) \times\left(n_w+n_d\right)}$, denoted $F_U\left(M, \Delta_1\right)$. The right figure shows an LFT with $\Delta_2 \in \mathbb{C}^{n_d \times n_e}$ in feedback around the lower channels of $M$, denoted $F_L\left(M, \Delta_2\right)$.

The upper LFT represents the following algebraic equations:
$$
\begin{gathered}
{\left[\begin{array}{l}
v \\
e
\end{array}\right]=\underbrace{\left[\begin{array}{ll}
M_{11} & M_{12} \\
M_{21} & M_{22}
\end{array}\right]}_{=M}\left[\begin{array}{l}
w \\
d
\end{array}\right]} \\
w=\Delta_1 v
\end{gathered}
$$
Substitute $w=\Delta_1 v$ into the first row of Equation 6 to obtain $v=M_{11} \Delta_1 v+M_{12} d$. If $I_{n_{\varepsilon}}-M_{11} \Delta_1$ is nonsingular then this equation can be solved for $v$ in terms of $d$ to yield $v=\left(I_{n_v}-M_{11} \Delta_1\right)^{-1} M_{12} d$. This also gives $w$ in terms of $d$ as $w=\Delta_1\left(I_{n_v}-M_{11} \Delta_1\right)^{-1} M_{12} d$. Substitute for $w$ into the second row of Equation 6 to obtain:
$$
e=\underbrace{\left[M_{22}+M_{21} \Delta_1\left(I_{n_v}-M_{11} \Delta_1\right)^{-1} M_{12}\right]}_{:=F_U\left(M, \Delta_1\right)} d
$$
To summarize, the upper LFT of $M$ and $\Delta_1$ is said to be well-posed if $I_{n_v}-M_{11} \Delta_1$ is nonsingular. If it is well-posed then $F_U\left(M, \Delta_1\right) \in \mathbb{C}^{n_\kappa \times n_d}$ is defined as in Equation 8. Similarly, the lower LFT of $M$ and $\Delta_2$ is said to be well-posed if $I_{n_e}-M_{22} \Delta_2$ is nonsingular. If it is well-posed then $F_L\left(M, \Delta_2\right) \in \mathbb{C}^{n_w \times n_w}$ is defined as:
$$
F_L\left(M, \Delta_2\right)=M_{11}+M_{12} \Delta_2\left(I_{n_{\varepsilon}}-M_{22} \Delta_2\right)^{-1} M_{21}
$$
The upper and lower LFTs were defined assuming $M, \Delta_1$, and $\Delta_2$ are complex matrices of compatible dimensions. The definitions remain valid when $M, \Delta_1$, and $\Delta_2$ are systems of compatible dimensions (assuming the interconnections are well-posed). The function lft computes LFTs of two matrices and/or systems. Specifically, Ift (Delta1,M) and lft (M,Delta2) compute the upper and lower LFTs shown in Figure 4.

---
## Ex
Example 4. Consider a real parameter $p \in[3.1,3.9]$. The normalized form is $p=3.5+0.4 \delta_p$ where $\delta_p \in[-1,1]$. This can be expressed as the upper LFT $p=F_U\left(M, \delta_p\right)$ with a $2 \times 2$ matrix $M=\left[\begin{array}{c}M_{11} M_{12} \\ M_{21} M_{22}\end{array}\right]$. To determine $M$, equate $F_U\left(M, \delta_p\right)$ (using the definition in Equation 8) to the normalized form for $p$ :
$$
3.5+0.4 \delta_p=M_{22}+\frac{M_{21} M_{12} \delta_p}{1-M_{11} \delta_p}
$$
This yields $M_{11}=0, M_{22}=3.5$, and $M_{21} M_{12}=0.4$. A valid LFT description for $p$ is given by $F_U\left(M, \delta_p\right)$ with $M=\left[\begin{array}{ll}0 & 0.4 \\ 1 & 3.5\end{array}\right]$. The "known" information for the uncertain parameter $p$ is the nominal value (interval center) of 3.5 and the uncertainty radius of 0.4 . These are captured in the matrix $M$. The "unknown" information is the precise value of $p$ which is captured by $\delta_p$. The LFT description separates this known from unknown information.

It is important to emphasize that the LFT description is not unique. Equation 10 uniquely defines the diagonal entries of $M$. However, it allows for freedom in choosing the off-diagonal above, and $M=\left[\begin{array}{cc}0 & 1 \\ 0.4 & 1.5\end{array}\right]$. In general, any matrix $M=\left[\begin{array}{cc}0 & 0.4 / d \\ d & 3.5\end{array}\right]$ with $d \neq 0$ is a valid choice.
The Matlab command lftdata can be used to extract the LFT description for an uncertainty. The code below shows an example for $p \in[3.1,3.9]$.

	% Create uncertain real parameter
	 p = ureal(’p’,3.5,’Range’,[3.1 3.9]);

	% Use "lftdata" to extract M and normalized uncertainty deltap
	 [M,deltap] = lftdata(p);
	 M
M = 	
	0           0.6325
	0.6325   3.5000

	 M(1,2)*M(2,1) % Product of off-diagonals = 0.4
ans = 	0.4000

	% Use "lft" to evaluate at specific normalized values
	 delta0 = -1; p0 = lft(delta0,M) % Returns left endpoint
ans = 	3.1000


	 delta0 = 0; p0 = lft(delta0,M) % Returns nominal (center)
ans =	3.5000

	 delta0 = 1; p0 = lft(delta0,M) % Returns right endpoint
ans =	3.9000

---
Example 5. Consider the complex uncertainty $\alpha$ in the symmetric disk $m$. The normalized form is $\alpha=\frac{1+m \delta}{1-m \delta}=1+\frac{2 m \delta}{1-m \delta}$ where $\delta \in \mathbb{C}$ satisfies $|\delta| \leq 1$. This can be expressed as the upper LFT $\alpha=F_U(M, \delta)$ with a $2 \times 2$, complex matrix $M=\left[\begin{array}{ll}M_{11} & M_{12} \\ M_{21} & M_{22}\end{array}\right]$. To determine $M$, equate $F_U(M, \delta)$ (using the definition in Equation 8) to the normalized form for $\alpha$ :
$$
1+\frac{2 m \delta}{1-m \delta}=M_{22}+\frac{M_{21} M_{12} \delta}{1-M_{11} \delta}
$$
This yields $M_{11}=m, M_{22}=1$, and $M_{21} M_{12}=2 m$. A valid LFT description for $\alpha$ is given by $F_U\left(M, \delta_p\right)$ with $M=\left[\begin{array}{cc}m & 2 m \\ 1 & 1\end{array}\right]$. Again, this choice is not unique, e.g. $M=\left[\begin{array}{cc}m \\ \sqrt{2 m} & 1\end{array}\right]$ is also a valid choice.

---
Example 6. Consider a dynamic LTI uncertainty in multiplicative form $\tilde{P}=P_0(1+W \Delta)$ where $P_0=\frac{1}{s+1}$ and $W=\frac{2 s+0.43}{s+8.67}$. The normalized uncertainty $\Delta$ is stable, LTI, and satisfies the bound $\|\Delta\|_{\infty} \leq 1$. This can be expressed as the upper LFT $p=F_U(M, \Delta)$ with a $2 \times 2$ system $M=\left[\begin{array}{cc}M_{11} M_{12} \\ M_{21} M_{22}\end{array}\right]$. To determine $M$, equate $F_U\left(M, \delta_p\right)$ (using the definition in Equation 8) to the normalized form for $\tilde{P}$. This yields $M_{11}=0, M_{22}=P_0$, and $M_{21} M_{12}=P_0 W$. A valid LFT description for $\tilde{P}$ is given by $F_U(M, \Delta)$ with $M=\left[\begin{array}{cc}0 & P_0 W \\ 1 & P_0\end{array}\right]$. The "known" information for the uncertain system $\tilde{P}$ is the nominal dynamics $P_0$ and the bound on the relative error $W$. These are captured in the matrix $M$. The "unknown" information is the precise value of the dynamics $\tilde{P}$ which is captured by $\Delta$. Again, the LFT description separates this known from unknown information. As noted previously, the LFT description is not unique. The off-diagonals are free to be chosen such that $M_{21} M_{12}=P_0 W$. One valid choice for $M$ is given above. Other valid choices are given by $M=\left[\begin{array}{cc}0 & \left(P_0 W\right) / d \\ d & P_0\end{array}\right]$ where $d$ is stable with a stable inverse. This requires $d$ to have relative degree zero.
