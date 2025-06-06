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

Let $A \in \mathbb{R}^{n \times n}$ and $Q \in \mathbb{R}^{n \times n}$ be given. The Lyapunov equation for these matrices is:
$$
A^T X+X A+Q=0
$$
This is a linear matrix equation in the unknown $X \in \mathbb{R}^{n \times n}$. The next lemma provides a sufficient condition for solvability of this equation.

Lemma 1. Let $A \in \mathbb{R}^{n \times n}$ and $Q \in \mathbb{R}^{n \times n}$ be given with $A$ Hurwitz. ${ }^{\dagger}$ The Lyapunov equation $A^T X+X A+Q=0$ has the unique solution:
$$
X:=\int_0^{\infty} e^{A^T t} Q e^{A t} d t=\int_0^{\infty} Z(t) d t
$$
Proof. First, the integral in Equation 3 is finite (and hence $X$ well-defined) because $A$ is assumed to be Hurwitz. Define the time-dependent matrix $Z(t):=e^{A^T t} Q e^{A t}$. The time derivative of $Z$ is given by:
$$
\begin{aligned}
\dot{Z}(t)=A^T Z(t)+Z(t) A \\
\end{aligned}
$$
Integrate both sides of this relation from $t=0$ to $t=\infty$ to obtain:
$$
-Q=\left.Z(t)\right|_{t=0} ^{\infty}=A^T X+X A
$$
This verifies that $X$ in Equation 3 solves the Lyapunov equation. Uniqueness of this solution can be shown by examining the dimensions of the domain and range of the matrix function $\Pi(X)=A^T X+X A$. See the proof of Theorem 4.1 in Dullerud and Paganini for details.
The expression in Equation 3 is useful to prove certain theoretical properties regarding Lyapunov equations and their solutions. For example, all the Lyapunov equations in the remainder of the notes will have $Q=Q^T$. It follows from Lemma 1 that if $Q=Q^T$ then $X=X^T$. It is important to emphasize that Lyapunov equations are typically not solved by evaluating the integral in Equation 3. Efficient numerical algorithms to solve the Lyapunov equation instead rely on certain eigenvalue decompositions. An early reference for such numerical algorithms is (Bartels and Stewart, Communications of the ACM, 1972).
It will also be useful to consider the following Lyapunov inequality:
$$
A^T X+X A+Q<0
$$
This is a linear matrix inequality in the unknown $X \in \mathbb{R}^{n \times n}$. The interpretation is that $A^T X+X A+Q$ is negative definite. The next lemma provides a connection between stability of an LTI system and solutions to related Lyapunov equalities / inequalities.

Lemma 2. Consider the (autonomous) linear time-invariant system:
$$
\dot{x}(t)=A x(t) , \quad \text{where}\quad e^{A t} x(0)=x(t)
$$
The following statements are equivalent:
1. The LTI system is stable ( $A$ is Hurwitz).
2. For any $Q \geq 0$ there exists $X \geq 0$ satisfying the Lyapunov equation $A^T X+X A+Q=0$. 
   Moreover, if $Q=C^T C \geq 0$ with $(A, C)$ observable then the solution satisfies $X>0$.
3. For any $Q \geq 0$ there exists $Y>0$ satisfying the Lyapunov inequality $A^T Y+Y A+Q<0$.

Finally, we note that solutions of the Lyapunov equations are minimal in the sense that they bound solutions of the Lyapunov inequality. This is made precise in the next lemma.
Lemma 3. Let $A \in \mathbb{R}^{n \times n}$ and $Q=Q^T \in \mathbb{R}^{n \times n}$ be given with $A$ Hurwitz. Assume $X \geq 0$ and $Y>0$ satisfy the Lyapunov equation $A^T X+X A+Q=0$ and the Lyapunov inequality $A^T Y+Y A+Q \leq 0$. Then $Y \geq X \quad \rightarrow \quad (Y-X) \geqslant 0$

Proof. Subtract the Lyapunov equation and inequality:
$$
A^T(Y-X)+(Y-X) A \leq 0
$$
Thus there is a matrix $\tilde{Q} \geq 0$ such that
$$
A^T(Y-X)+(Y-X) A+\tilde{Q}=0 \quad \text { y } ֶ X
$$
$A$ is Hurwitz so it follows from statement $2 \mathrm{ff}$ Lemma 7 that $Y-X \geq 0$.

Assume $A$ is Hurwitz. If $Q=0$ then $X=0$ solves the Lyapunov equation $A^T X+X A=0$. Thus Lemma 3 implies that any $Y$ satisfying the Lyapunov inequality $A^T Y+Y A \leq 0$ must be positive semidefinite $Y \geq 0$.

---
†A matrix $A$ is defined to be Hurwitz if all of its eigenvalues have strictly negative real parts.
‡This paper describes an algorithm to solve a more general equation $A X+X B+Q=0$ where $A, B$, and $Q$ are given square matrices. This is known as the Sylvester equation. The required computation estimated by the number of floating point operations (multiply, divide, add, etc) grows roughly with $n^3$.