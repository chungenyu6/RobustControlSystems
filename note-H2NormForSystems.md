---
Note Status:
  - 🌱0
Note Type:
  - 📄note
Source Type:
  - 🏫lecture
tags:
  - control
  - linear_algebra
---
# Metadata
Source URL       : [UMN/EE5235: Robust Multivariable Control Systems]
Author              : [[Nicola Elia]]
Related Note     : [[02-SystemNorms]]


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

Other system norms have useful applications in control design and analysis, e.g. see Section 4.10 in Skogestad / Postlethwaite. This section briefly introduces another commonly used system norm. Define the $\mathcal{H}_2$ norm of a stable, $n_y \times n_u$ LTI system $P$ as:
$$
\|P\|_2:=\sqrt{\frac{1}{2 \pi} \int_{-\infty}^{\infty} \sum_{i=1}^{n_y} \sum_{k=1}^{n_u}\left|P_{i, k}(j \omega)\right|^2 d \omega}
$$
If the system has non-zero feedthrough $(D \neq 0)$ then $\|P\|_2=\infty$. Thus $P$ must be strictly proper $(D=0)$ to have finite $\mathcal{H}_2$ norm. The $\mathcal{H}_2$ norm can be equivalently expressed as: ${ }^{\text {}}$
$$
\|P\|_2=\sqrt{\frac{1}{2 \pi} \int_{-\infty}^{\infty} \sum_{i=1}^{\min \left(n_y, n_u\right)} \sigma_i(P(j \omega))^2 d \omega}
$$
This form indicates that the $\mathcal{H}_2$ norm is the sum of singular values integrated across frequency. This norm accounts for all frequencies and all input directions of the system. This is in contrast to the $\mathcal{H}_{\infty}$ norm which only depends on the worst frequency (max over $\omega$ ) and worst input direction (maximum singular value).

The $\mathcal{H}_{\infty}$ has a time-domain interpretation as the induced $\mathcal{L}_2$ norm. The $\mathcal{H}_2$ norm also has several useful time-domain interpretations. These interpretations require a few additional facts regarding Fourier Transforms given in the appendix [[202304271720-FourierTransforms]]. First consider the special case where $P$ is a stable LTI system with a single input, i.e. $P$ has dimension $n_y \times 1$. Let $y:[0, \infty) \rightarrow \mathbb{R}^{n_y}$ denote the impulse response of $P$. The $\mathcal{H}_2$ norm of $P$ is equal to the $\mathcal{L}_2$ norm of the impulse response $y$. This is verified as follows:
$$
\begin{aligned}
\|y\|_2^2 & =\frac{1}{2 \pi} \int_{-\infty}^{\infty}\|\hat{y}(j \omega)\|_2^2 d \omega \\
& =\frac{1}{2 \pi} \int_{-\infty}^{\infty}\|P(j \omega)\|_2^2 d \omega \\
& =\frac{1}{2 \pi} \int_{-\infty}^{\infty} \sum_{i=1}^{n_y}\left|P_i(j \omega)\right|^2 d \omega \\
& =\|P\|_2^2
\end{aligned}
$$
A similar result can be derived for systems with multiple inputs.
The $\mathcal{H}_2$ norm also has a stochastic interpretation. Consider a stable, $n_y \times n_u$ LTI system $P$ (with possibly more than one input). Let the input $u$ be white noise with unit variance,
$E\left[u(t) u(\tau)^T\right]=I \delta(t-\tau)$. The $\mathcal{H}_2$ norm is equal to the power (expected root mean square) in the output when the system is drive by unit variance white noise. In particular, when $y(t)$ reaches steady state then $\|P\|_2=\sqrt{E\left[y(t)^T y(t)\right]}$. This stochastic interpretation is useful in many control design and analysis problems. For example, wind gusts acting on an aircraft can be modeled as a random process. A Dryden model is a standard model for wind gusts as an output of an LTI system driven by white noise. Sensor models can also be modeled by white noise processes.

Finally, note that the $\mathcal{H}_2$ norm is not induced by any signal norm. In particular, consider the identity system $P=I$. This can be viewed as a state-space system with feedthrough $D=I$ and no state dimension. This identity system maps any input $u$ back to itself $y=u$. It follows from the definition that $\|I\|_{2 \rightarrow 2}=1$. Moreover, $\|I\|=1$ for any system norm induced by the same input/output signal norm. The $\mathcal{H}_2$, on the other hand, has $\|I\|_2=\infty$. Hence the $\mathcal{H}_2$ norm is not induced by any signal note. It can also be shown that the $\mathcal{H}_2$ norm is not sub-multiplicative (e.g. see Example 4.19 in Skogestad and Postlethwaite).

---
'Let $\operatorname{Tr}(\cdot)$ denote the trace, i.e. sum of the diagonal entries of a square matrix. If $M \in \mathbb{C}^{n \times m}$ then $\sum_{i, j}\left|M_{i, j}\right|^2=\operatorname{Tr}\left(M^* M\right)$. Let $U \Sigma V^*$ be the SVD of $M$ so that $M^* M=V \Sigma^* \Sigma V^*$. Finally use the fact that $\operatorname{Tr}(A B)=\operatorname{Tr}(B A)$ for any matrices of compatible dimensions to show:
$$
\sum_{i, j}\left|M_{i, j}\right|^2=\operatorname{Tr}\left(V \Sigma^* \Sigma V^*\right)=\operatorname{Tr}\left(\Sigma^* \Sigma V^* V\right)=\sum_i \sigma_i(M)^2
$$
