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


Consider an LFT $F_U(L, \Delta)$ and partition $L=\left[\begin{array}{ll}L_{11} 1 & L_{12} \\ L_{21} & L_{22}\end{array}\right]$. This LFT defines a matrix/system mapping input $d$ to output $e$ by the following equations:
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
d
\end{array}\right] \\
w & =\Delta v
\end{aligned}
$$
If $L_{22}$ is nonsingular, then the second row of Equation 20 can be solved for $d$ :
$$
d=-L_{22}^{-1} L_{21} w+L_{22}^{-1} e
$$
This can be substituted into the first row of Equation 20 to obtain an LFT $F_u(M, \Delta)$ mapping input $e$ and output $d$ :
$$
\begin{aligned}
{\left[\begin{array}{l}
v \\
d
\end{array}\right] } & =\underbrace{\left[\begin{array}{cc}
L_{11}-L_{12} L_{22}^{-1} L_{21} & L_{12} L_{22}^{-1} \\
-L_{22}^{-1} L_{21} & L_{22}^{-1}
\end{array}\right]}_{:=M}\left[\begin{array}{l}
w \\
e
\end{array}\right] \\
w & =\Delta v
\end{aligned}
$$
This result was derived using an upper LFT but a similar formula can be obtained for the inverse of a lower LFT. There is one technical point regarding these inverses. The initial LFT $F_U(L, \Delta)$ is well-posed if $I-L_{11} \Delta$ is nonsingular. Nonsingularity of $L_{22}$ implies that we can define $M$ as in Equation 23. However, well-posedness of $F_U(M, \Delta)$ requires the additional condition that $I-M_{11} \Delta$ is nonsingular.

Example 7. Consider a real parameter $p \in[3.1,3.9]$. The normalized form is $p=3.5+0.4 \delta_p$ where $\delta_p \in[-1,1]$. It was shown previously that this uncertainty can be expressed as $F_U\left(L, \delta_p\right)$ with $L:=\left[\begin{array}{cc}0 & \sqrt{0.4} \\ \sqrt{0.4} & 3.5\end{array}\right] . \quad L_{22}=3.5$ is nonzero and hence the LFT inverse can be formed as $F_U\left(L, \delta_p\right)$ where $L:=\left[\begin{array}{cc}-0.11 & 0.18 \\ -0.18 & 0.29\end{array}\right]$. The inverse $F_U\left(L, \delta_p\right)$ can be interpreted as an LFT model for $\frac{1}{p}=\frac{1}{3.5+0.4 \delta_p}$. Below is a simple Matlab code demonstrating this example

	 p = ureal(’p’,3.5,’range’,[3.1 3.9]);
	 [L,deltap] = lftdata(p); L
L =
	0           0.6325
	0.6325   3.5000

	 pinv = 1/p;
	 [M,deltap] = lftdata(pinv); M
M =
-0.1143   0.1807
-0.1807   0.2857