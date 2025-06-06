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

This section briefly reviews a few results on algebraic Riccati equations (AREs). Details can be found in Chapter 13 of ZDG and Chapter 6 of DP.

Let $A \in \mathbb{R}^{n \times n}, Q=Q^T \in \mathbb{R}^{n \times n}$, and $R=R^T \in \mathbb{R}^{n \times n}$ be given. The ARE associated with $(A, Q, R)$ is:
$$
A^T X+X A+Q+X R X=0
$$
This is a quadratic matrix equation in the $n \times n$ matrix unknown $X$. If $n=1$, then this corresponds to the (scalar) quadratic equation $r x^2+2 a x+q=0$. This has two (real or complex) solutions depending the values of $(a, q, r)$. Similarly, the matrix ARE has multiple (real or complex) solutions. Typically it will be required to find a particular solution $X=X^T \in \mathbb{R}^{n \times n}$ such that $A+R X$ is Hurwitz. This is called the (real, symmetric) stabilizing solution. Such a solution, if it exists, will be unique.
Define the Hamiltonian matrix $H \in \mathbb{R}^{2 n \times 2 n}$ associated with $(A, Q, R)$ as:
$$
H:=\left[\begin{array}{cc}
A & R \\
-Q & -A^T
\end{array}\right]
$$
Note that ARE can be equivalently written in terms of this Hamiltonian:
$$
\left[\begin{array}{ll}
X & -I
\end{array}\right] H\left[\begin{array}{c}
I \\
X
\end{array}\right]=0
$$
The eigenspace of $H$ plays a key role in solving the ARE. ${ }^{\S}$ The next result provides a sufficient condition for the existence of a stabilizing solution of the ARE. It is essentially Theorem 6.5 in DP. The proof involves straight-forward but lengthy linear algebra arguments.
Lemma 4. Let $A \in \mathbb{R}^{n \times n}, Q=Q^T \in \mathbb{R}^{n \times n}$, and $R=R^T \in \mathbb{R}^{n \times n}$ be given. Assume:
1. The associated Hamiltonian $H$ has no purely imaginary axis eigenvalues.
2. $R \geq 0$ or $R \leq 0$
3. $(A, R)$ is stabilizable
Then the ARE associated with $(A, Q, R)$ has a unique solution $X=X^T \in \mathbb{R}^{n \times n}$ such that $A+R X$ is Hurwitz.

The section introduced the ARE associated with matrices $(A, Q, R)$. It will also be useful to consider the following strict algebraic Riccati inequality (ARI):
$$
A^T X+X A+Q+X R X<0
$$
This is a quadratic matrix inequality in the unknown $X \in \mathbb{R}^{n \times n}$.

---
${ }^{\S}$ Define $J:=\left[\begin{array}{cc}0 & -I \\ I & 0\end{array}\right]$ and note that $J^{-1}=-J$. Directly verify, by multiplication, that $H=J\left(-H^*\right) J^{-1}$. $H$ and $-H^*$ are similar and have the same eigenvalues. Thus the eigenvalues of $H$ are symmetric about the imaginary axis, i.e. $\lambda$ is an eigenvalue if and only if $-\lambda^*$ is an eigenvalue.


