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

This section briefly reviews a few definitions and facts regarding sign definite matrices. These will be stated for complex Hermitian matrices $M=M^*$. However, similar definitions and facts hold for real symmetric matrices $M=M^T$. First, recall the definitions for sign definite Hermitian matrices.
Definition 1. Let $M=M^* \in \mathbb{C}^{n \times n}$ be given.
1. The matrix $M$ is positive definite, denoted $M>0$, if $v^* M v>0$ for all nonzero $v \in \mathbb{C}^n$.
2. The matrix $M$ is positive semidefinite, denoted $M \geq 0$, if $v^* M v \geq 0$ for all $v \in \mathbb{C}^n$.
3. The matrix $M$ is negative definite, denoted $M<0$, if $v^* M v<0$ for all nonzero $v \in \mathbb{C}^n$.
4. The matrix $M$ is negative semidefinite, denoted $M \leq 0$, if $v^* M v \leq 0$ for all $v \in \mathbb{C}^n$.
5. The matrix $M$ is sign indefinite if it is neither positive nor negative semidefinite.
The matrix $M$ is assumed, in these definitions, to be Hermitian. Thus notation for sign definite matrices, e.g. $M>0$, implies $M=M^*$ even if this assumption is not explicitly stated. This notation can be generalized: if $M=M^*$ and $N=N^*$ then $M>N$ denotes that $M-N>0$. Similar definitions are used for $M \geq N, M<N$, and $M \leq N$. If neither $M \geq N$ nor $M \leq N$ holds then the matrices $M$ and $N$ are not comparable.

Next, it can be shown that any Hermitian matrix (not necessarily sign definite) has real eigenvalues. Let $(\lambda, v)$ be an eigenpair of $M=M^*$ so that $M v=\lambda v$ for some non-zero $v$. The eigenvector can be scaled to be unit norm $\|v\|=v^* v=1$. This gives:
$$
\lambda=v^* M v=v^* M^* v=(M v)^* v=\lambda^*
$$
The second equality uses $M=M^*$. Thus the eigenvalue is equal to its own conjugate, i.e. it is real. The sign definiteness of a matrix $M=M^*$ can be characterized in terms of its real eigenvalues $\left\{\lambda_i(M)\right\}_{i=1}^n \subset \mathbb{R}$. Specifically, $M>0$ if and only if $\lambda_i(M)>0$ for $i=1, \ldots, n$. Moreover, $M \geq 0$ if and only if $\lambda_i(M) \geq 0$ for $i=1, \ldots, n$. Similarly, a matrix is negative definite (semidefinite) if and only if all eigenvalues are negative (non-positive).
The following is a short collection of useful facts regarding Hermitian matrices:
1. If $M=M^* \in \mathbb{C}^{n \times n}$ then there exists a diagonal matrix $\Lambda \in \mathbb{R}^{n \times n}$ and a square unitary matrix $U \in \mathbb{C}^{n \times n}$ such that $M=U \Lambda U^*$. This is an eigenvalue decomposition of $M$. $\Lambda$ contains the real eigenvalues along the diagonals and the columns of $U$ contain the eigenvectors. The eigenvectors are orthonormal because $U$ is unitary, $U^* U=I$.
2. If $M \geq 0$ then there exists a matrix square root $M^{\frac{1}{2}} \geq 0$ such that $M=M^{\frac{1}{2}} M^{\frac{1}{2}}$. If $M>0$ then $M^{\frac{1}{2}}>0$. A construction is given as follows. Let $M=U \Lambda U^*$ denote the eigenvalue decomposition for $M$ where $\Lambda$ is a diagonal matrix containing the eigenvalues of $M$. These are are non-negative by assumption. Define $M^{\frac{1}{2}}:=U \Lambda^{\frac{1}{2}} U^*$ where $\Lambda^{\frac{1}{2}}$ is a diagonal matrix with the $(i, i)$ entry given by $\sqrt{\Lambda_{i, i}}$.
3. Let $M \in \mathbb{C}^{n \times n}$ be given with $M>0$. Then $N^* M N \geq 0$ for any $N \in \mathbb{C}^{n \times n}$. Moreover, if $N$ is nonsingular then $N^* M N>0$. This is called a congruence transformation from $M$ to $N^* M N$. More generally, $N^* M N \geq 0$ for any $N \in \mathbb{C}^{n \times m}$ and $N^* M N>0$ if $N$ has full column rank.