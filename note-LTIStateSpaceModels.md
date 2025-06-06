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
Related Note     : [[02-LTISystems]], [[02-MIMORobustness]]


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

As reviewed previously, classical frequency-domain control design primarily uses ODE/TF models of an LTI system $P$. A related representation for $P$ is given by an $n^{\text {th }}$ order, statespace model:
$$
\begin{aligned}
& \dot{x}(t)=A x(t)+B u(t) \\
& y(t)=C x(t)+D u(t) \\
& \text { Initial Condition (IC): } x(0):=x_0
\end{aligned}
$$
where $x \in \mathbb{R}^{n_x}$ is the state, $u \in \mathbb{R}^{n_u}$ is the input, and $y \in \mathbb{R}^{n_y}$ is the output. The ODE/TF models used in classical control design are typically SISO. The state-space formulation naturally translates to MIMO models $\left(n_u>1\right.$ and/or $\left.n_y>1\right)$.

The state-space representation is not unique. Two state-space models $(A, B, C, D)$ and $(\tilde{A}, \tilde{B}, \tilde{C}, \tilde{D})$, possibly with different state dimensions, are said to be equivalent if their (zero IC) forced response is identical for all inputs. A state-space model is said to be a minimal realization if it has the smallest state dimension among all equivalent realizations. Controllability and observability are important properties for state-space models. It is sufficient here to recall that a state-space model is minimal if and only if it is both controllable and observable. Finally, recall that if $T \in \mathbb{R}^{n_x \times n_x}$ is a nonsingular matrix then the change of coordinates $z:=T x$ yields another state-space model with state matrices $\left(T A T^{-1}, T B, C T^{-1}, D\right)$. These coordinate transformations change the (internal) state representation of the model but yield the same relationship from input $u$ to output $y$.

It is possible to convert from an ODE/TF model for $P$ into an equivalent state-space model, e.g. using the controllable or observable canonical form. It is also possible to convert from a state-space model into an equivalent ODE/TF model. Specifically, the transfer function associated with the state-space model in Equation 1 is:
$$
P(s)=C(s I-A)^{-1} B+D
$$
All state-space models related by nonsingular coordinate transformations yield the same transfer function representation. The transfer function is a complex function $P: \mathbb{C} \rightarrow \mathbb{C}^{n_y \times n_u}$ with rational dependence on $s \in \mathbb{C}$. If the system is MIMO then the transfer function, evaluated at any $s$, is an $n_y \times n_u$ matrix $P(s)$. This can be interpreted as a matrix of SISO transfer function with $P_{i j}(s)$ representing the dynamics from input $j$ to output $i$.

Regarding stability, we can define BIBO stability with a state-space model as before: $P$ is bounded BIBO stable if the output response is uniformly bounded for any uniformly bounded input and zero (state) initial conditions. We can also introduce another definition of internal stability related to the free (IC) response.

Definition 1. The linear system $P$ is internally stable if the free response state converges asymptotically to zero $(x(t) \rightarrow 0$ as $t \rightarrow \infty)$ for every (state) initial condition. The system is called unstable otherwise.

The state-space model is internally stable if and only if all eigenvalues of the state matrix $A$ have strictly negative real part. If the state-space model is minimal then the eigenvalues of the state matrix are equivalent to the poles of the corresponding TF. Thus the various notions of stability defined for ODE/SS/TF models are equivalent if the models are minimal.



