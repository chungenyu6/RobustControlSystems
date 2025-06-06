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
Related Note     : [[02-DiskMargins]]


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

Let $\operatorname{Disk}\left(I_L, I_R\right)$ denote the open disk in the complex plane with diameter on the real axis corresponding to the interval $\left(I_L, I_R\right)$. For example, Disk $(c-r, c+r)$ denotes an open disk centered at $c$ with radius $r$. The minimum distance from Nyquist curve of $L$ to -1 is $d_{\min }$. Hence the Nyquist curve of $L$ has the properties: (i) it does not enter the interior of Disk(-1$\left.d_{\text {min }},-1+d_{\text {min }}\right)$ at any frequency, (ii) at some frequency it touches the boundary of Disk(-1$\left.d_{\text {min }},-1+d_{\text {min }}\right)$. As an example, consider the loop $L(s)=\frac{2}{s^3+2 s^2+3 s-1}$ shown in Figure 1. For - this loop, $S$ is stable and $\|S\|_{\infty}=1.62$ with the peak gain achieved at the frequency $\omega=1.1 \frac{\mathrm{rad}}{\mathrm{sec}}$. The disk corresponding to $d_{\min }=\frac{1}{\|S\|_{\infty}}=0.62$. is shown (shaded green) in Figure 3 for this loop. The Nyquist curve of $L$ does not enter the interior of this disk and just touches the disk boundary at the frequency $\omega=1.06 \frac{\mathrm{rad}}{\mathrm{sec}}$.

![[Pasted image 20230427135610.png|500]]

The Nyquist curve $L$ is excluded from entering the interior of $\operatorname{Disk}\left(-1-d_{\min },-1+d_{\min }\right)$ and hence this is called a Nyquist exclusion disk. This exclusion implies robustness to simultaneous gain and phase variations in the plant. Consider the feedback diagram shown in Figure 4. $P(s)$ is again the "nominal" model used to design the controller $C(s)$. The constant $\alpha \in$ $\mathbb{C}$ is introduced to represent variations in the plant dynamics. The complex variations can be presented in polar form as $\alpha=g e^{-j \theta}$ for some real numbers $g, \theta$. Thus $\alpha$ represents simultaneous gain and phase variations. The nominal $(\alpha=1)$ and perturbed open-loop transfer functions are denoted as $L(s)=P(s) C(s)$ and $L_\alpha(s)=\alpha P(s) C(s)$, respectively. Similarly, the nominal $(\alpha=1)$ and perturbed closed-loop sensitivity functions are denoted as $S(s)=\frac{1}{1+L(s)}$ and $S_\alpha(s)=\frac{1}{1+L_\alpha(s)}$

The next theorem relates the minimum distance to the amount of gain/phase variation that can be tolerated without loss of stability. The theorem is stated in terms of $\|S\|_{\infty}=\frac{1}{d_{\min }}$.

![[Pasted image 20230427135642.png|400]]

Theorem 1. Assume $C$ stabilizes the nominal model $P$ and let $m \leq 1$ be given. Then $C$ stabilizes the perturbed model $\alpha P$ for all $\alpha \in \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right){ }^{\S}$ if and only if $\|S\|_{\infty} \leq \frac{1}{m}$.

Proof. It can be shown, via complex algebra, that the (open) Disk $\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ is equivalent to following set of complex numbers:
$$
\complement \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)=\left\{\frac{1}{1-z}: z \in \mathbb{C} \text { with }|z|<m\right\} .
$$
This fact is used twice in the proof below.
   $(\Leftarrow)$ Assume $\|S\|_{\infty} \leq \frac{1}{m}$ and hence $|1+L(j \omega)| \geq m$ for all $\omega$. By Equation 6 , any $\alpha \in \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ can be expressed as $\alpha=\frac{1}{1-z}$ with $|z|<m$. Thus the corresponding perturbed loop $L_\alpha$ satisfies:
$$
\begin{aligned}
|1+\alpha L(j \omega)| & =\left|1+\frac{1}{1-z} L(j \omega)\right| \\
& =\frac{1}{|1-z|} \cdot|1+L(j \omega)-z| \\
& \geq \frac{1}{|1-z|} \cdot(|1+L(j \omega)|-|z|)
\end{aligned}
$$
   The second line follows from algebraic manipulation and the third line follows from the triangle inequality. This result along with $|z|<m$ and $|1+L(j \omega)| \geq m$ imply $|1+\alpha L(j \omega)|>0$. To summarize, $\|S\|_{\infty} \leq \frac{1}{m}$ implies that $L_\alpha(\omega) \neq-1$ for all $\alpha \in D i s k\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ and for all $\omega$.

The next part of the proof follows from a Nyquist argument and is briefly sketched. The nominal loop $L$ encircles -1 the "correct" number of times because $C$ is assumed to stabilize $P$. Specifically, the number of counter-clockwise encirclements of -1 by the Nyquist loop of $L$ must equal the number of RHP poles of the open-loop $L$. It was just shown that $L_\alpha(j \omega) \neq-1$ for all perturbations and all frequencies. It must be that $L_\alpha$ encircles -1 the same number of times as $L$ (otherwise $L_\alpha(j \omega)$ would pass through -1 for some $\alpha$ and $\omega$ ). Thus $L_\alpha$ also encircles -1 the "correct" number of times because both $L$ and $L_\alpha$ have the same number of (open-loop) right-half plane poles. This verifies that $C$ stabilizes the perturbed model $\alpha P$ for all $\alpha \in \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$

   $(\Rightarrow)$ This direction is shown by contradiction. Assume $\|S\|_{\infty}>\frac{1}{m}$ so that $\left|1+L\left(j \omega_0\right)\right|<m$ at some frequency $\omega_0$. In other words, there is a complex number $z$ such that
$$
1+L\left(j \omega_0\right)=z \text { and }|z|<m<1
$$
   Define $\alpha:=\frac{1}{1-z}$ and note that $\alpha \in \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ by Equation 6. Moreover, Equation 5 can be re-arranged to show $1+\alpha L\left(j \omega_0\right)=0$. This implies that the perturbed sensitivity function $S_\alpha$ has a pole at $s=j \omega_0$. Thus $\|S\|_{\infty}>\frac{1}{m}$ implies the perturbed model $\alpha P$ is not stabilized by $C$ for some $\alpha \in \operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$.

This result is one type of robust stability theorem. Specifically, $\|S\|_{\infty} \leq \frac{1}{m}$ is equivalent to robust stability with respect to all gain and phase variations $\alpha$ in the uncertainty set $\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$. The largest disk is defined with $\bar{m}_S:=\frac{1}{\|S\|_{\infty}}$ and $\bar{m}_S$ is the disk margin defined based on the sensitivity $S$. Technically $\bar{m}_S \leq 1$ is required to apply the theorem. This is the typical case because $\|S\|_{\infty} \geq 1$ in any real feedback system. For example, the open loop gain in a real feedback system rolls off at high frequencies $(|L(j \omega)| \rightarrow 0$ as $\omega \rightarrow \infty)$. As a result, $|S(j \omega)| \rightarrow 1$ as $\omega \rightarrow \infty)$

If the nominal sensitivity $S$ has a large gain then $\bar{m}_S \ll 1$ and this uncertainty disk only contains small variations from the nominal value $\alpha=1$. Conversely, smaller values of $\|S\|_{\infty}$ give rise to larger values for the margin $\bar{m}_S$ and hence robustness to a larger set of uncertainty. Note that there are two related but different disks defined by this margin $\bar{m}_S$. First, $\|S\|_{\infty} \leq \frac{1}{\bar{m}_S}$ is equivalent to $d_{\min } \geq \bar{m}_S$. This defines the set $\operatorname{Disk}\left(-1-\bar{m}_S,-1+\bar{m}_S\right)$ that excludes the Nyquist curve $L$. This Nyquist exclusion disk is equivalent, by the theorem above, to robust stability for all variations $\alpha$ in the uncertainty set $\operatorname{Disk}\left(\frac{1}{1+\bar{m}_S}, \frac{1}{1-\bar{m}_S}\right)$.

---
${ }^{\S}$ Note that as $m \rightarrow 1$ the open set Disk $\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$ converges to the open half-plane $\left\{z: \operatorname{Re}(z)>\frac{1}{2}\right\}$.