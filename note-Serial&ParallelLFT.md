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

![[Pasted image 20230427171134.png|500]]

Consider the serial interconnection of two LFTs $F_U\left(L, \Delta_1\right)$ and $F_U\left(N, \Delta_2\right)$ as shown on the left of Figure 5. Partition $L=\left[\begin{array}{ll}L_{11} & L_{12} \\ L_{21} & L_{22}\end{array}\right]$ and $N=\left[\begin{array}{ll}N_{11} & N_{12} \\ N_{21} & N_{22}\end{array}\right]$. The algebraic equations for the two individual LFTs are:
$$
\begin{aligned}
& {\left[\begin{array}{l}
v_1 \\
e_1
\end{array}\right]=\left[\begin{array}{ll}
L_{11} & L_{12} \\
L_{21} & L_{22}
\end{array}\right]\left[\begin{array}{l}
w_1 \\
d_1
\end{array}\right] \text { and } w_1=\Delta_1 v_1} \\
& {\left[\begin{array}{l}
v_2 \\
e_2
\end{array}\right]=\left[\begin{array}{ll}
N_{11} & N_{12} \\
N_{21} & N_{22}
\end{array}\right]\left[\begin{array}{l}
w_2 \\
d_2
\end{array}\right] \text { and } w_2=\Delta_1 v_2}
\end{aligned}
$$

The serial connection feeds the output of the first LFT as the input to the second LFT, i.e. $d_2=e_1$. This yields a combined LFT $F_U(M, \Delta)$ as shown on the right of Figure 5 where:
$$
\left[\begin{array}{l}
v_1 \\
v_2 \\
e_2
\end{array}\right]:=\underbrace{\left[\begin{array}{ccc}
L_{11} & 0 & L_{12} \\
N_{12} L_{21} & N_{11} & N_{12} L_{22} \\
N_{22} L_{21} & N_{21} & N_{22} L_{22}
\end{array}\right]}_{:=M}\left[\begin{array}{l}
w_1 \\
w_2 \\
d_1
\end{array}\right] \text { and }\left[\begin{array}{l}
w_1 \\
w_2
\end{array}\right]:=\underbrace{\left[\begin{array}{cc}
\Delta_1 & 0 \\
0 & \Delta_2
\end{array}\right]}_{:=\Delta}\left[\begin{array}{l}
v_1 \\
v_2
\end{array}\right]
$$
Note that uncertainties $\Delta_1$ and $\Delta_2$ in the individual LFTs combine into a single uncertainty $\Delta$ with block diagonal structure. In other words, the combined uncertainty $\Delta$ is "structured" as certain entries are known to be zero.

This connection was derived assuming a connection of two "upper" LFTs. Similar results can be derived if one or both systems is a "lower" LFT. In addition, similar connections can be derived for parallel connections. These are defined by feeding the same input into $F_U\left(L, \Delta_1\right)$ and $F_U\left(N, \Delta_2\right)$, i.e. $d_1=d_2$, and then summing their outputs, i.e. $e=e_1+e_2$.
