---
Note Status:
  - 🔅1
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
Related Note     : [[02-LTISystems]] 

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

<u>Valuable insight</u> into the system dynamics can be obtained by understanding the relations between the following <u>properties of the response</u>: 
- Coefficients of the ODE
- Locations of the poles and zeros in the complex plane and, for complex poles/zeros, their associated damping ratio $\zeta$ and natural frequency $\omega_n$
- Stability and response characteristics often with a focus on the step response characteristics including steady-state value, rise time, settling time, overshoot, and (in some cases) undershoot. 

This section briefly reviews two notions of stability for an LTI system $P$. The free (initial condition) response of the ODE is a solution $y$ with $u(t)=0$ for all $t \geq 0$. The first notion of stability is stated in terms of this free response.



## Internally Stable

**Definition 1.** The linear system $P$ is internally stable if the free response <u>converges asymptotically to zero</u> $(y(t) \rightarrow 0$ as $t \rightarrow \infty)$ for every initial condition. The system is called unstable otherwise.
The following theorem provides a condition for stability.

**Theorem 1.** A linear system is internally stable if and only if all roots of the characteristic equation have strictly negative real part, i.e. $\operatorname{Re}\left(p_k\right)<0$ for all $k=1, \ldots, n$ where Re denotes the real part of the root.
In other words, $P$ is internally stable if and only if all roots are in the strict left half of the complex plane (strict LHP). An alternative notion for stability is characterized in terms of bounded input-output responses. Specifically, a signal $f: \mathbb{R}_{\geq 0} \rightarrow \mathbb{R}$ is uniformly bounded if there is a constant $M<\infty$ such that $|f(t)| \leq M$ for all $t \geq 0$. The second notion of stability is formalized in the next definition.

## BIBO Stable

**Definition 2.** The linear system $P$ is bounded input-bounded output (BIBO) stable if the output response is uniformly bounded for any uniformly bounded input and zero initial conditions.
For minimal ODE models the two definitions of stability are equivalent. This is stated without proof in the next theorem.

**Theorem 2.** Let a linear system $P$ be modeled by a minimal $O D E$. Then $P$ is internally stable if and only if it is BIBO stable.

## Conclusion

For minimal ODEs, internal stability (with zero input and non-zero initial conditions) is equivalent to input-output stability (with zero initial conditions and non-zero outputs). Thus we won't distinguish between them when using the term "stable".
