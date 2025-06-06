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


Figure 2 shows a feedback system that includes the signals required to model these issues. The systems include the plant $P$ and controller $C$. The signals include the reference command $r$, tracking error $e$, control command $u$, input disturbance $d$, plant input $v$, plant output $y$, sensor noise $n$, and measured plant output $m$. Most applications will have competing design requirements related to the various signals shown in this generic feedback diagram.

![[Pasted image 20230427105254.png|400]]

Each input / output pair in Figure 2 has an associated transfer function that models the dynamics from the chosen input to output. For example, the transfer function from input $r$ to output $y$, denoted by $T_{r \rightarrow y}(s)$, can be computed by setting $d=0$ and $n=0$ in Figure 2. This yields $T_{r \rightarrow y}(s)=\frac{P(s) C(s)}{1+P(s) C(s)}$. As one additional example, the transfer function from input $r$ to output $e$ is given by $T_{r \rightarrow e}(s)=\frac{1}{1+P(s) C(s)}$. These two transfer functions have special significance. In particular, $S(s)=\frac{1}{1+P(s) C(s)}$ is called the sensitivity transfer function and $T(s)=\frac{P(s) C(s)}{1+P(s) C(s)}$ is the complementary sensitivity function. ${ }^{\S}$ The name for $S(s)$ arises because this transfer function is a measure of the sensitivity of the closed-loop to small changes in the plant model $P(s)$." In addition, $T(s)$ is "complementary" to $S(s)$ in the sense that the sum to one, i.e. $S(s)+T(s)=1$ for all values of $s \in \mathbb{C}$.

The feedback diagram contains three input signals $(r, d, n)$ and five "internal" signals that can be selected as outputs $(e, u, v, y, m)$. Thus there are a total of $15(=3 \cdot 5)$ possible input / output transfer functions. All 15 possible input / output transfer functions can be expressed in terms of $S$ and $T$ as shown in the following matrix array:
$$
\left[\begin{array}{l}
Y(s) \\
U(s) \\
E(s) \\
M(s) \\
V(s)
\end{array}\right]=\left[\begin{array}{ccc}
T(s) & -T(s) & P(s) S(s) \\
C(s) S(s) & -C(s) S(s) & -T(s) \\
S(s) & -S(s) & -P(s) S(s) \\
T(s) & S(s) & P(s) S(s) \\
C(s) S(s) & -C(s) S(s) & S(s)
\end{array}\right]\left[\begin{array}{c}
R(s) \\
N(s) \\
D(s)
\end{array}\right]
$$
This array should be interpreted using standard matrix multiplication. For example, the second output $U(s)$ is given by the second row of the matrix multiplied by the input vector:
$$
U(s)=C(s) S(s) R(s)-C(s) S(s) N(s)-T(s) D(s)
$$
This formula is a consequence of the principle of superposition for linear systems. The individual effects of the inputs $(r, n, d)$ are summed together to determine their combined effect on the output.

---

${ }^{\S}$ The notation $T(s)$ with no subscript will always denote the complementary sensitivity. If a subscript appears, e.g. $T_{r \rightarrow y}(s)$, then it denotes the input and output pair. $d P$ in the plant model causes a differential change $d T$ in $T$. A measure of the system sensitivity is $\frac{d T / T}{d P / P}$. This is the relative change in the closed loop divided by a relative change in the plant dynamics. This can be rewritten as $\frac{d T}{d P} \cdot \frac{P}{T}$. The derivative is given by:
$$
\frac{d T}{d P}=\frac{d}{d P}\left[\frac{P C}{1+P C}\right]=\frac{C}{(1+P C)^2}
$$
Substituting this derivative yields $\frac{d T}{d P} \cdot \frac{P}{T}=S$. In other words, $S(s)$ measures the sensitivity of the closed-loop (from $r$ to $y$ ) to small (differential) changes in the plant model.


