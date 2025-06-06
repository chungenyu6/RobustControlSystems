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

The $\mathcal{L}_2$ norm for signals can be used to define an induced norm on systems. Consider an LTI system $P$ with input $u:[0, \infty) \rightarrow \mathbb{R}^{n_u}$ and output $y:[0, \infty) \rightarrow \mathbb{R}^{n_y}$. Assume $P$ has a state-space representation with state $x$. The output $y$ depends on both the the input $u$ and the initial condition $x(0)$. The induced $\mathcal{L}_2$ norm for $P$ is loosely defined as the maximum input/output gain $\frac{\|y\|_2}{\|u\|_2}$. There are two technical issues. First, if $P$ is unstable and minimal then inputs $u \in \mathcal{L}_2$ can generate unbounded outputs with $\|y\|_2=\infty$. This case yields infinite gain. Second, a zero input $\left(\|u\|_2=0\right)$ can generate a non-zero output $\left(\|y\|_2>0\right)$ due to the initial condition. This situation (which also yields infinite gain) is avoided by considering only the zero initial condition response. If $x(0)=0$ then: (i) $y$ depends linearly on $u,{ }^{\ddagger}$ and (ii) zero input $\left(\|u\|_2=0\right)$ generates zero output $\left(\|y\|_2=0\right)$.
The induced $\mathcal{L}_2$ norm for an LTI system $P$ is formally defined as:
$$
\|P\|_{2 \rightarrow 2}:=\max _{\substack{0 \neq u \in \mathcal{L}_2 \\ x(0)=0}} \frac{\|P u\|_2}{\|u\|_2}
$$
As noted above, $\|P\|_{2 \rightarrow 2}=\infty$ if a minimal realization of $P$ has unstable modes. On the other hand, $\|P\|_{2 \rightarrow 2}<\infty$ if $P$ is stable. The $\mathcal{L}_{\infty}$ norm was previously defined for an LTI system $P$ as the peak on a singular value plot: $\|P\|_{\infty}=\max _\omega \bar{\sigma}(P(j \omega))$. If $P$ is stable then this is called the $\mathcal{H}_{\infty}$-norm. The next theorem states that the induced $\mathcal{L}_2$ and $\mathcal{H}_{\infty}$ norms are, in fact, equal for stable systems.

Theorem 1. If $P$ is a stable, LTI system then $\|P\|_{2 \rightarrow 2}=\|P\|_{\infty}$.

Proof. The equality is demonstrated by showing $\|P\|_{2 \rightarrow 2} \geq\|P\|_{\infty}$. and $\|P\|_{2 \rightarrow 2} \leq\|P\|_{\infty}$. A sketch of the proof is provided here and additional details can be found in other textbooks, e.g. Zhou/Doyle/Glover or Dullerud/Paganini.

First show $\|P\|_{2 \rightarrow 2} \geq\|P\|_{\infty}$. This is done by constructing an input $u \in \mathcal{L}_2$ such that the the output $y$ satisfies $\frac{\|y\|_2}{\|u\|_2} \approx\|P\|_{\infty}$. The construction starts by selecting $\omega_p$ as the peak frequency on a singular value plot for $P$, i.e. such that $\|P\|_{\infty}=\bar{\sigma}\left(P\left(j \omega_p\right)\right)$. s $^{\S}$ Then there exist vectors $\bar{u} \in \mathbb{C}^{n_u}$ and $\bar{y} \in \mathbb{C}^{n_y}$ such that $\bar{y}=P\left(j \omega_p\right) \bar{u},\|\bar{u}\|_2=1$, and $\|\bar{y}\|_2=\|P\|_{\infty}$. Next recall that if $u(t)=\bar{u} e^{j \omega_p t}$ then $y(t)=y_{\text {tran }}(t)+\bar{y} e^{j \omega_p t}$ where $y_{\text {tran }}(t)$ is a transient that decays to zero. It can be shown that $\left\|y_{\text {tran }}\right\|_2<\infty$. The amplitude vectors of the steady-state response have, by construction, a gain of $\frac{\|\bar{y}\|_2}{\|\bar{u}\|_2}=\|P\|_{\infty}$. A remaining technical point is that the input $u$ is not in $\mathcal{L}_2$ because $\|u\|_2=\infty$. Instead, define a truncated version of the input:
$$
u_T(t)=\left\{\begin{array}{cc}
\bar{u} e^{j \omega_p t} & \text { for } t \in[0, T] \\
0 & \text { else }
\end{array}\right.
$$
The $\mathcal{L}_2$ norm of the truncated input signal is $\left\|u_T\right\|_2=\sqrt{T} \cdot\|\bar{u}\|_2$. This yields an output $y_T$ which is not necessarily zero for $t>T$. However, this output $y_T$ on $t \in[0, T]$ is $y_T(t)=y_{\text {tran }}(t)+\bar{y} e^{j \omega_p t}$.

This can be used to obtain the lower bound $\left\|y_T\right\|_2 \geq \sqrt{T} \cdot\|\bar{y}\|_2-\left\|y_{\text {tran }}\right\|_2$. Hence the gain $\frac{\left\|y_T\right\|_2}{\left\|u_T\right\|_2} \rightarrow\|P\|_{\infty}$ as $T \rightarrow \infty$. The induced $\mathcal{L}_2$ norm for $P$ is the maximum gain over all possible $\mathcal{L}_2$ inputs. It must be no smaller than the gain achieved with the specific choice $u_T$ as $T \rightarrow \infty$, i.e. $\|P\|_{2 \rightarrow 2} \geq\|P\|_{\infty}$. This proof used complex sinusoids but it can be extended to real sinusoids.

Next show $\|P\|_{2 \rightarrow 2} \leq\|P\|_{\infty}$. This step requires a few additional facts regarding Fourier Transforms. These are provided in the appendix of this set of notes [[202304271720-FourierTransforms]]. Let $\hat{u}$ and $\hat{y}$ denote the Fourier Transforms for an input $u \in \mathcal{L}_2$ and its corresponding output $y$. The $\mathcal{L}_2$ norm of the output can be bounded as follows:
This bound holds for any $u \in \mathcal{L}_2$ and hence $\|P\|_{2 \rightarrow 2} \leq\|P\|_{\infty}$.
Finally, note that given two systems $P_1$ and $P_2$ it follows that $\left\|P_1 P_2\right\|_{2 \rightarrow 2} \leq\left\|P_1\right\|_{2 \rightarrow 2}$. $\left\|P_2\right\|_{2 \rightarrow 2}$. In other words, the induced $\mathcal{L}_2$ norm is sub-multiplicative. In addition, for any system $P$ and signal $u$ it follows, by definition, that $\|P u\|_2 \leq\|P\|_{2 \rightarrow 2}\|u\|_2$. These properties will be applied when considering robustness of feedback systems.

---
${ }^{\ddagger}$ Let $y_i(i=1,2)$ denote the zero initial condition response of $P$ due to inputs $u_i(i=1,2)$. Then for any $c_1, c_2 \in \mathbb{R}$ the zero initial condition response due to the input $u=c_1 u_1+c_2 u_2$ is given by $y=c_1 y_1+c_2 y_2$. Thus the zero initial condition output responses combine linearly.
${ }^{\S}$ The proof assumes $\omega_p<\infty$ and must be modified slightly if the peak occurs as $\omega \rightarrow \infty$.

