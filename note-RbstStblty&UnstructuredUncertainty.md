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

A robust stability theorem with unstructured, complex uncertainty was derived in a previous set of notes using the small gain theorem. This section will derive a related result but for unstructured, dynamic uncertainty. This will highlight the connections between complex and dynamic uncertainty. The result will be given using the LFT framework for modeling uncertainty. This sets the stage for the more general result with unstructured uncertainty.
The previous section recast the calculation of the robust stability margin to the problem of finding the "smallest" $\Delta$ such that $\operatorname{det}\left(I-M_{11}\left(s_0\right) \Delta\left(s_0\right)\right)=0$ for some $s_0$ in closed RHP. The next lemma is a related linear algebra result for complex matrices. This will be used to provide the robust stability margin for systems.

Lemma 2. Let $M \in \mathbb{C}^{n_v \times n_w}$ be given. Then $\operatorname{det}(I-M \Delta) \neq 0$ for all $\Delta \in \mathbb{C}^{n_w \times n_v}$ with $\bar{\sigma}(\Delta)<m$ if and only if $\bar{\sigma}(M) \leq \frac{1}{m}$

Proof. $(\Leftarrow)$ Assume that $\bar{\sigma}(M) \leq \frac{1}{m}$. Recall that the maximum singular value is equal to the matrix induced $2-2$ norm. Thus $\bar{\sigma}(M \Delta) \leq \bar{\sigma}(M) \bar{\sigma}(\Delta)<1$ for all $\Delta$ with $\bar{\sigma}(\Delta)<m$. This bound further implies that $\|M \Delta v\|<\|v\|$ for any non-zero vector $v \in \mathbb{C}^{n_v}$. Equivalently, $(I-M \Delta) v \neq 0$ for any non-zero vector $v$. Hence $I-M \Delta$ is nonsingular for all $\bar{\sigma}(\Delta)<m$.
$(\Rightarrow)$ This direction is shown by contradiction. Assume $\bar{\sigma}(M)>\frac{1}{m}$. The SVD of $M$ gives vectors $v \in \mathbb{C}^{n_v}, w \in \mathbb{C}^{n_w}$ such that:
$$
\bar{\sigma}(M) \cdot v=M w \text { and }\|v\|_2=\|w\|_2=1
$$

Select $\Delta_0:=\frac{1}{\bar{\sigma}(M)} w v^*$ and note that $\bar{\sigma}\left(\Delta_0\right)=\frac{1}{\bar{\sigma}(M)}{ }^{\dagger}$ By construction, $\left(I-M \Delta_0\right) v=0$ and thus $I-M \Delta_0$ is singular, i.e. $\operatorname{det}\left(I-M \Delta_0\right)=0$.

One additional connection is needed before stating the robust stability margin theorem for unstructured dynamic uncertainty. The next two lemmas demonstrate that complex uncertainty can be interpolated at any finite, non-zero frequency using a stable, dynamic system. In addition, the dynamic uncertainty has norm no larger than the chosen complex uncertainty. Lemmas 3 and 4 are stated for scalar (SISO) and MIMO uncertainty, respectively. These lemmas provide the link between complex and dynamic uncertainty for robustness analysis.
Lemma 3. Let a finite frequency $\omega_0>0$ and a complex number $\delta_0 \in \mathbb{C}$ be given. There exists a stable, LTI system $\Delta(s)$ such that $\Delta\left(j \omega_0\right)=\delta_0$ and $\|\Delta\|_{\infty} \leq\left|\delta_0\right|$.

Lemma 4. Let a finite frequency $\omega_0>0$ and a rank-one complex matrix $\Delta_0=w_0 v_0^* \in \mathbb{C}^{n_w \times n_v}$ be given. There exists an $n_w \times n_v$ stable, LTI system $\Delta(s)$ such that $\Delta\left(j \omega_0\right)=\Delta_0$ and $\|\Delta\|_{\infty} \leq \bar{\sigma}\left(\Delta_0\right)$

Lemma 4 is restricted to rank-one complex matrices as this will be sufficient for the robust stability margin theorem. The proofs for these lemmas use basic linear systems theory. However, the constructions are a bit involved and hence they are given in the appendix. Note that both lemmas assume a finite, nonzero frequency $0<\omega_0<\infty$. An LTI system with real-valued state matrices has real frequency response at $\omega_0=0$ and $\infty$, i.e. $\Delta(0), \Delta(\infty) \in \mathbb{R}^{n_v \times n_w}$. Hence it is not possible to fit an arbitrary complex uncertainty with an LTI system at these frequencies. Thus the equivalence between complex and dynamic uncertainty breaks down at $\omega_0=0$ and $\infty$.

The next theorem is the main result for uncertain systems with dynamic, unstructured uncertainty. It provides an exact, necessary and sufficient condition for the robust stability margin of such systems.

Theorem 1. Consider an uncertain system $F_U(M, \Delta)$ where $\Delta$ is an unstructured, stable LTI system. Assume the uncertain system is nominally stable. The uncertain system is well-posed and stable for all $\|\Delta\|_{\infty}<m$ if and only if $\left\|M_{11}\right\|_{\infty}:=\max _{\omega \in \mathbb{R} \cup\{\infty\}} \bar{\sigma}\left(M_{11}(j \omega)\right) \leq \frac{1}{m}$.

Proof. $(\Leftarrow)$ Assume that $\left\|M_{11}\right\|_{\infty} \leq \frac{1}{m}$ and let $\Delta$ be any stable LTI with $\|\Delta\|_{\infty}<m$. Apply Lemma 2 to conclude $\operatorname{det}\left(I-M_{11}(j \omega) \Delta(j \omega)\right) \neq 0$ for all $\omega \in \mathbb{R} \cup\{\infty\}$. In particular, $\operatorname{det}(I-$ $\left.M_{11}(\infty) \Delta(\infty)\right) \neq 0$ and hence $F_U(M, \Delta)$ is well-posed. By Lemma $1, \operatorname{det}\left(I-M_{11}(j \omega) \Delta(j \omega)\right) \neq$ 0 implies that $F_U(M, \Delta)$ has no poles on the imaginary axis. Thus $F_U(M, \Delta)$ is both well-posed and has no imaginary axis poles for all $\|\Delta\|_{\infty}<m$.

Next, suppose there is a stable LTI $\Delta$ with $\|\Delta\|_{\infty}<m$ such that $F_U(M, \Delta)$ has a pole at $s_0$ in the strict RHP. Consider the scaled perturbation $\beta \Delta$ for $\beta \in[0,1]$. A state-space realization of $F_U(M, \beta \Delta)$ can be derived as in Section 1. For the special case that $M$ has no feedthrough ( $D=0)$, the state 'matrix $\bar{A}(\beta)$ of $F_U(M, \beta \Delta)$ is:
$$
\bar{A}(\beta)=\left[\begin{array}{cc}
A+\beta B_1 D_{\Delta} C_1 & \beta B_1 C_{\Delta} \\
B_{\Delta} C_1 & A_{\Delta}
\end{array}\right]
$$
At $\beta=0$ the poles of $F_U(M, \beta \Delta)$ are located at the eigenvalues of $A$ and $A_{\Delta}$. These are in the LHP because both $M$ and $\Delta$ are stable. At $\beta=1, F_U(M, \beta \Delta)$ has, by assumption, a pole in the strict RHP. The eigenvalues of $\bar{A}(\beta)$ are continuous functions of $\beta$. Hence the poles move from the LHP to the strict RHP as $\beta$ is varied from zero to one. By continuity, the poles must cross the imaginary axis for some $0<\beta<1$. This implies that $F_U(M, \beta \Delta)$ has imaginary axis poles and $\|\beta \Delta\|_{\infty}<m$. However, it was just shown that this is not possible. Hence the uncertain system is well-posed and stable for all $\|\Delta\|_{\infty}<m$
$(\Rightarrow)$ This direction is shown by contradiction. Assume $\left\|M_{11}\right\|_{\infty}>\frac{1}{m}$. Hence there is a finite frequency $\omega_0>0$ such that $\bar{\sigma}\left(M_{11}\left(j \omega_0\right)\right)>\frac{1}{m}$. Apply Lemma 2 to conclude there exists $\Delta_0 \in \mathbb{C}^{n_w \times n_v}$ with $\bar{\sigma}\left(\Delta_0\right)<m$ and $\operatorname{det}\left(I-M_{11}\left(j \omega_0\right) \Delta_0\right)=0$. In fact, $\Delta_0$ can be constructed as a rank one matrix based on the proof of Lemma 2. By Lemma 4 there exists an $n_w \times n_v$ stable, LTI system $\Delta(s)$ such that $\Delta\left(j \omega_0\right)=\Delta_0$ and $\|\Delta\|_{\infty} \leq \bar{\sigma}\left(\Delta_0\right)<m$. It is possible that the uncertain system $F_U(M, \Delta)$ is not well-posed. However, if $F_U(M, \Delta)$ is well-posed then $\operatorname{det}\left(I-M_{11}\left(j \omega_0\right) \Delta\left(j \omega_0\right)\right)=0$ implies that it has a pole at $j \omega_0$ by Lemma 1. Thus for some $\Delta$ with $\|\Delta\|_{\infty}<m$ the uncertain system $F_U(M, \Delta)$ is either not well-posed or is unstable.

The interpolation results (Lemma 3 and 4) require a finite, non-zero frequency $\omega_0$. If $M_{11}$ achieves its peak gain at $\omega_0=0$ then the interpolation is performed at a (small) non-zero frequency. The gain of $M_{11}$ at the non-zero frequency is slightly reduced compared to the peak gain but this allows for the interpolation construction. Similarly if $M_{11}$ achieves its peak gain at $\omega_0=\infty$ then the interpolation is performed at a (large) finite frequency.


---
${ }^{\dagger} F o r$ any vectors $x$ and $y^*$ it can be shown, using the definition of the maxtrix induced $2-2$ norm that $\bar{\sigma}\left(x y^*\right)=\|x\|\|y\|$.


---
## Ex

![[Pasted image 20230427180724.png|400]]

Example 1. Consider the feedback system in Figure 2 with an $n_y \times n_u$ plant $P$. An $n_u \times n_u$ perturbation $\alpha=I_{n_u}+\Delta$ is introduced at the plant input. $\Delta$ is assumed to be an unstructured stable, LTI uncertainty. The uncertain closed-loop system from input $r$ to output $e$ is represented by the $\operatorname{LFT} F_U(M, \Delta)$ where:
$$
\left[\begin{array}{l}
v \\
e
\end{array}\right]=\underbrace{\left[\begin{array}{cc}
C P_0\left(I_{n_u}+C P_0\right)^{-1} & C\left(I_{n_y}+P_0 C\right)^{-1} \\
P_0\left(I_{n_u}+C P_0\right)^{-1} & \left(I_{n_y}+P_0 C\right)^{-1}
\end{array}\right]}_{:=M}\left[\begin{array}{l}
w \\
r
\end{array}\right]
$$
$M$ can be rewritten in terms of input/output sensitivities as $M=\left[\begin{array}{cc}T_I & C S_O \\ P_0 S_I & S_O\end{array}\right]$. In particular, $M_{11}=T_I$. Assume the feedback loop is nominally stable. By Theorem 1 the uncertain system is well-posed and stable for all $\|\Delta\|_{\infty}<m$ if and only if $\left\|T_I\right\|_{\infty} \leq \frac{1}{m}$. A similar result was presented earlier for complex uncertainty.

---
Example 2. DRAFT: Provide specific example (include weight?). Note that large maximum singular means small stability margin, i.e. poor robustness. Also note that we can place the poles at any frequency by proper choice of Delta. Thus a sigma plot of $M_{11}$ provides additional frequency domain info, i.e. where the magnitude is large the robustness to uncertainty at that frequency is small. The peak value of this magnitude plot is inversely related to the stability margin. Moreover, this gives a collection of bad perturbations (one for each frequency) that can be studied further in a high fidelity simulation. This complements Monte Carlo techniques. These points will be important when we move to more general structured stability margins.
The proof provides a construction for a perturbation $\Delta_0$ from the maximum singular value of $M$ and its corresponding singular vectors. This construction can be performed in the following two lines of code:

	[U,S,V] = svd(M);
	Delta0 = (-1/S(1,1))*V(:,1)*U(:,1)’;