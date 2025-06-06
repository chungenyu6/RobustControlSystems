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
Related Note     : [[02-LinearSystemsTheory]]


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


The next lemma provides a connection between the $H_{\infty}$ norm of an LTI system and solutions to related AREs/ARIs. This result is known as the Bounded Real (or KYP) lemma. The lemma is stated for systems with no feedthrough $(D=0)$ to simplify the notation. The proof is briefly sketched below and additional details are given by Lemma 7.3 of DP.
Lemma 5. Consider the linear time-invariant system $G$ :
$$
\begin{aligned}
\dot{x}(t) & =A x(t)+B d(t) \\
e(t) & =C x(t)
\end{aligned}
$$
Let $\gamma>0$ be given. The following statements are equivalent:
1. The LTI system $G$ is stable ( $A$ is Hurwitz) and $\|G\|_{\infty}<\gamma$.
2. There exists a unique $X \geq 0$ such that $A+\gamma^{-2} B B^T X$ is Hurwitz and satisfying the ARE:
$$
A^T X+X A+C^T C+\gamma^{-2} X B B^T X=0
$$
3. There exists $Y>0$ satisfying the strict ARI:
$$
A^T Y+Y A+C^T C+\gamma^{-2} Y B B^T Y<0
$$

Proof.
$(\mathbf{1} \Rightarrow \mathbf{2})$ : The Hamiltonian associated with the ARE in Equation 24 is:
$$
H:=\left[\begin{array}{cc}
A & \gamma^{-2} B B^T \\
-C^T C & -A^T
\end{array}\right]
$$
Roughly, the assumptions for $G$ imply that this Hamiltonian has no imaginary axis eigenvalues (as shown in the homework). Then apply Lemma 4 to conclude that the ARE has a unique solution such that $A+\gamma^{-2} B B^T X$ is Hurwitz. Finally, the ARE can be re-written as:
$$
A^T X+X A=-\left(C^T C+\gamma^{-2} X B B^T X\right) \leq 0
$$
By Lemma 3 (and the subsequent comment), the Lyapunov inequality $A^T X+X A \leq 0$ and $A$ Hurwitz imply $X \geq 0$.
$(2 \Rightarrow 3)$ : Let $X \geq 0$ be the unique stabilizing solution to the ARE so that $A+\gamma^{-2} B B^T X$ is Hurwitz. It follows from Lemma 2 that there exists $\tilde{Y}>0$ such that
$$
\left(A+\gamma^{-2} B B^T X\right)^T \tilde{Y}+\tilde{Y}\left(A+\gamma^{-2} B B^T X\right)<-I
$$
Define $Y:=X+\epsilon \tilde{Y}$ and note that $Y>0$ for all $\epsilon>0$. Multiply Equation 22 by $\epsilon$, add to the ARE (Equation 24), and complete the square. This yields:
$$
A^T Y+Y A+C^T C+\gamma^{-2} Y B B^T Y=-\epsilon I+\epsilon^2 \gamma^{-2} \tilde{Y} B B^T \tilde{Y}
$$
Choose $\epsilon>0$ sufficiently small so that the right side is negative definite. Then $Y>0$ satisfies the strict ARI.
$(3 \Rightarrow 1)$ : The ARI can be re-written as:
$$
A^T Y+Y A<-C^T C-\gamma^{-2} Y B B^T Y \leq 0
$$
Thus $Y>0$ also satisfies the Lyapunov inequality and $A$ is Hurwitz by Lemma 2. Next, let $\omega \geq 0$ be a finite frequency. Add and subtract a factor of $j \omega Y$ to the ARI:
$$
-(j \omega I-A)^* Y-Y(j \omega I-A)+C^T C+\gamma^{-2} Y B B^T Y<0
$$
Define $Z:=(j \omega I-A)^{-1} B$ and multiply this inequality on the left and right by $Z^*$ and $Z$. This congruence transformation yields:
$$
-Z^* Y B-B^T Y Z+G(j \omega)^* G(j \omega)+\gamma^{-2} Z^* Y B B^T Y Z<0
$$
Here $G(j \omega)=C(j \omega I-A)^{-1} B$ is the frequency response function of the LTI system. Complete the square:
$$
G(j \omega)^* G(j \omega)-\gamma^2 I+\underbrace{\gamma^2\left(\gamma^{-2} B^T Y Z-I\right)^*\left(\gamma^{-2} B^T Y Z-I\right)}_{\geq 0}<0
$$
It follows that $G(j \omega)^* G(j \omega)<\gamma^2 I$ and hence $\bar{\sigma}(G(j \omega))<\gamma$. This holds for any finite frequency $\omega \geq 0$ and $G(\infty)=0$ by assumption. Thus $\|G\|_{\infty}<\gamma$.

The proof of $(3 \Rightarrow 1)$ uses the ARI and algebraic manipulations to show the frequency domain inequality $G(j \omega)^* G(j \omega)<\gamma^2 I$. This demonstrates that $\gamma$ is a (strict) bound on the $\sigma$-plot of $G$. There is an alternative time-domain proof. Let $Y>0$ be any solution to the ARI. The ARI is a strict inequality and $Y>0$ satisfies the following perturbed ARI hence for a sufficiently small $\epsilon>0$ :
$$
A^T Y+Y A+C^T C+(\gamma-\epsilon)^{-2} Y B B^T Y<0
$$
Let $\tilde{\gamma}:=\gamma-\epsilon$ denote the slightly perturbed gain. Define the function $V: \mathbb{R}^n \rightarrow \mathbb{R}$ by $V(x)=x^T Y x$. Let $x(t)$ and $e(t)$ be the state and output response of the linear system $G$ with the input $d \in L_2$ and initial condition $x(0)=0$. Differentiating $V(x(t))$ with respect to time yields:
$$
\begin{aligned}
\frac{d V}{d t}(x(t)) & =(A x(t)+B d(t))^T Y x(t)+x(t)^T Y(A x(t)+B d(t)) \\
& =x(t)^T\left(A^T Y+Y A\right) x(t)+d(t)^T B^T Y x(t)+x(t)^T Y B d(t)
\end{aligned}
$$
Substitute using the perturbed ARI and complete the square to obtain:
$$
\frac{d V}{d t}(x(t)) \leq-e(t)^T e(t)+\tilde{\gamma}^2 d(t)^T d(t)-\tilde{\gamma}^2\left(d(t)-\tilde{\gamma}^{-2} B^T Y x(t)\right)^T\left(d(t)-\tilde{\gamma}^{-2} B^T Y x(t)\right)
$$

Integrate from $t=0$ to $t=T$ :
$$
V(x(T))-V(x(0))+\int_0^T e(t)^T e(t) d t \leq \tilde{\gamma}^2 \int_0^T d(t)^T d(t) d t
$$
$V(x(0))=0$ by the initial condition $x(0)=0 . V(x(T)) \geq 0$ by the assumption $Y>0$. Let $T \rightarrow \infty$ to conclude that $e \in L_2$ and $\|e\|_2 \leq \tilde{\gamma}\|d\|_2<\gamma\|d\|_2$. Thus the induced $L_2$ norm of $G$ is strictly less than $\gamma . V$ is called a storage function and the proof is based on dissiaptivity theory. This time-domain proof can be extended to provide sufficient conditions to bound the norm of more general classes of systems, e.g. time-varying and/or nonlinear systems.