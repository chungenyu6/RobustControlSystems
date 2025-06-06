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
Related Note     : [[02-MIMORobustness]]


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

Recall that the forced (output) response of a state-space model due an initial condition $x(0)=$ $x_0$ and input $u$ is given by:
$$
y(t)=C e^{A t} x_0+\int_0^t C e^{A(t-\tau)} B u(\tau) d \tau+D u(t)
$$
Here $e^{A t}$ is the matrix exponential. This solution can be used to derive the frequency response due to a sinusoidal input. First consider the case with a complex sinusoidal forcing: $u(t)=\bar{u} e^{j \omega t}$ with $\omega \in \mathbb{R}$ as the frequency and $\bar{u} \in \mathbb{C}^{n_u}$ as the complex amplitude vector. Substitute this input $u$ into Equation 3 and re-arrange to obtain:
$$
y(t)=C e^{A t} x_0+C e^{A t}\left[\int_0^t e^{(j \omega I-A) \tau} d \tau\right] B \bar{u}+D u(t)
$$
Evaluate the integral in brackets:
$$
\int_0^t e^{(j \omega I-A) \tau} d \tau=(j \omega I-A)^{-1}\left[e^{(j \omega I-A) t}-I\right]
$$
Use this integral and the matrix relation $e^{A t}(j \omega I-A)^{-1}=(j \omega I-A)^{-1} e^{A t}$ to simplify Equation 4 to the following form:
$$
y(t)=C e^{A t}\left(x_0-(j \omega I-A)^{-1} B \bar{u}\right)+\underbrace{\left[C(j \omega I-A)^{-1} B+D\right]}_{=P(j \omega)} u(t)
$$

If the system $P$ is stable then $e^{A t} \rightarrow 0$ as $t \rightarrow \infty$. Hence the first term is a transient and only the second term remains in the steady-state.

To summarize, if $P$ is stable and $u(t)=\bar{u} e^{j \omega t}$ then the steady-state output response is:
$y(t) \rightarrow \bar{y} e^{j \omega t}$ where $\bar{y}:=P(j \omega) \bar{u}$
Thus the steady-state output oscillates at the same frequency as the input. The output has a (complex) amplitude vector $\bar{y}$ obtained by scaling the input amplitude $\bar{u}$ by $P(j \omega)$. The transfer function completely describes the response of the system to complex sinusoids. As a special case, if $\omega=0$ then $y(t) \rightarrow \bar{y}$ where $\bar{y}=P(0) \bar{u}$. The DC gain $P(0)$ is a real $n_y \times n_u$ matrix that governs the response to constant (real or complex) input vectors $\bar{u}$.

This complex frequency response can be interpreted in terms of real signals. Consider the following real sinusoidal input:
$$
u(t):=\left[\begin{array}{c}
a_1 \sin \left(\omega t+\phi_1\right) \\
\vdots \\
a_{n_u} \sin \left(\omega t+\phi_{n_u}\right)
\end{array}\right]
$$

All entries of the vector input $u$ oscillate at frequency $\omega$. Each entry can have a different (real) amplitude $a_k \in \mathbb{R}$ and (real) phase $\phi_k \in \mathbb{R}$. This input can be expressed as the imaginary part of a complex sinusoid:
$$
u(t)=\operatorname{Im}\left\{\bar{u} e^{j \omega t}\right\} \text { where } \bar{u}:=\left[\begin{array}{c}
a_1 e^{j \phi_1} \\
\vdots \\
a_{n_u} e^{j \phi_{n_u}}
\end{array}\right]
$$
The steady state response due to the complex input $\bar{u} e^{j \omega t}$ is $\bar{y} e^{j \omega t}$ where $\bar{y}=P(j \omega) \bar{u}$. It follows from the principle of superposition that the response due to the real input $u(t)=\operatorname{Im}\left\{\bar{u} e^{j \omega t}\right\}$ is $y(t)=\operatorname{Im}\left\{\bar{y} e^{j \omega t}\right\}$. Finally, assume the $k^{t h}$ entry of $\bar{y}$ is given in polar form as $b_k e^{j \psi_k}$. Then the steady-state output due to the real sinusoid $u(t)$ is given by:
$$
y(t) \rightarrow \operatorname{Im}\left\{\left[\begin{array}{c}
b_1 e^{j\left(\omega t+\psi_1\right)} \\
\vdots \\
b_{n_y} e^{j\left(\omega t+\psi_{n_y}\right)}
\end{array}\right]\right\}=\left[\begin{array}{c}
b_1 \sin \left(\omega t+\psi_1\right) \\
\vdots \\
b_{n_y} \sin \left(\omega t+\psi_{n_y}\right)
\end{array}\right]
$$