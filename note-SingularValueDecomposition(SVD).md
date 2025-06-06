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
Related Note     : [[02-map-LinearAlgebra]], [[02-MIMORobustness]]
[[05-DimensionalityReduction]]

---


There are several different matrix decompositions that appear in systems and control. For example, the eigenvalue decomposition of the state matrix $A$ is useful because stability can be determined from the corresponding eigenvalues. The singular value decomposition (SVD), introduced below, is another decomposition. It is useful for understanding the frequency response properties of a MIMO system. The following notation is used: If $A \in \mathbb{C}^{m \times n}$ then $A^*$ denotes the complex conjugate transpose of $A$, i.e. the $(i, j)$ entry of $A^*$ is given by the complex conjugate of the $(j, i)$ entry of $A$.

Theorem 1 (Singular Value Decomposition). Any matrix $M \in \mathbb{C}^{n \times m}$ can be decomposed as $M=U \Sigma V^*$ where:
1. $U \in \mathbb{C}^{n \times n}$ is a unitary matrix, i.e. $U^* U=U U^*=I_n$.
2. $V \in \mathbb{C}^{m \times m}$ is a unitary matrix, i.e. $V^* V=V V^*=I_m$.
3. $\Sigma \in \mathbb{R}^{n \times m}$ is a rectangular diagonal matrix of the form:
$$
\begin{gathered}
\qquad \Sigma=\left[\begin{array}{ll}
\hat{\Sigma} & 0_{n \times(m-n)}
\end{array}\right] \text { if } m \geq n \text { or } \Sigma=\left[\begin{array}{c}
\hat{\Sigma} \\
0_{(n-m) \times m}
\end{array}\right] \text { if } n>m \\
\text { with } \hat{\Sigma}=\operatorname{diag}\left(\sigma_1, \sigma_2, \ldots, \sigma_k\right) \in \mathbb{R}^{k \times k}, k=\min (m, n) \text {, and } \sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_k \geq 0 .
\end{gathered}
$$
The real, non-negative numbers $\left\{\sigma_i\right\}_{i=1}^k$ are the singular values of the matrix $M$. The maximum and minimum singular values are denoted as $\bar{\sigma}:=\sigma_1$ and $\underline{\sigma}:=\sigma_k$.

The matrix $U$ satisfies $U^* U=I_n$ and hence its columns, denoted $\left\{u_i\right\}_{i=1}^n$, are orthonormal. In other words $u_i^* u_i=1$ and $u_i^* u_j=0$ if $j \neq i$. Similarly, the columns of $V$, denoted $\left\{v_i\right\}_{i=1}^m$, are also orthonormal. This can be used to show the following relation:
$$
M v_i=\sigma_i u_i \text { for } i=1, \ldots, k
$$
The vectors $u_i$ and $v_i$ are the left (output) and right (input) singular vectors associated with singular value $\sigma_i$.

It is also useful to relate the singular values of $M$ to the eigenvalues of $M^* M$. First note:
$$
M^* M=\left(U \Sigma V^*\right)^*\left(U \Sigma V^*\right)=V\left(\Sigma \Sigma^*\right) V^*
$$
$V$ is unitary and hence $V^*$ is the inverse of $V$. Thus $V \hat{\Sigma}^2 V^*$ is an eigenvalue decomposition for $M^* M \in \mathbb{C}^{m \times m}$. Let $\lambda_i\left(M^* M\right)(i=1, \ldots m)$ denote the eigenvalues for $M^* M$. The first $k$ eigenvalues are $\lambda_i\left(M^* M\right)=\sigma_i(M)^2(i=1, \ldots k)$ with corresponding eigenvectors $v_i$. It follows similarly that $\lambda_i\left(M M^*\right)=\sigma_i(M)^2(i=1, \ldots k)$ with corresponding eigenvectors $u_i$.

Finally, the SVD provides a useful interpretation for the multiplication of a vector $w \in \mathbb{C}^m$ by a matrix $M \in \mathbb{C}^{n \times m}$. This multiplication $y=M w$. can be decomposed into three steps (Figure 1):
1. Rotation $z=V^* w$ : The Euclidean norm of $w$ is defined as $\|w\|_2:=\sqrt{\sum_{i=1}^m\left|w_i\right|^2}$ where $w_i$ is the $i^{t h}$ element of $w$. The multiplication $z=V^* w$ is a rotation in the sense that it does not change the Euclidean norm:
$$
\|w\|_2^2=w^* w=z^* V^* V z=z^* z=\|z\|^2
$$
2. Scaling $x=\Sigma z$ : The first $k$ entries of $x$ are obtained by scaling the corresponding entries of $z$ by the singular values, i.e. $x_i=\sigma_i z_i$ for $i=1, \ldots, k$.
3. Rotation $y=U w:$ Again, this preserves the Euclidean norm $\|y\|_2=\|U w\|_2$.

![[Pasted image 20230427142555.png|400]]

