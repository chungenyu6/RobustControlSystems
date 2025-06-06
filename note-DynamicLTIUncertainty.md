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
Related Note     : [[02-UncertaintyModeling]]


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

![[Pasted image 20230427165525.png|500]]

The left side of Figure 3 shows experimental frequency responses $\left\{P_i\right\}_{i=1}^N$ (blue) from a collection of $N$ different electro-mechanical systems. A low-order, approximate model $P_0$ (red) is also shown. At very low frequencies $(\leq 1 \mathrm{rad} / \mathrm{sec})$, all experimental results show the features of a double integrator $\frac{c}{s^2}$. The low-order model matches these results closely. At very high frequencies $(\geq 3 \mathrm{rad} / \mathrm{sec})$, the experimental results have substantial variation and the loworder model fails to capture these dynamics. The low-order model is reasonably accurate in the middle frequencies $(\approx 1-3 \mathrm{rad} / \mathrm{sec})$ but variations in the experimental data are apparent. This modeling situation is often encountered in feedback design where a low-order model is used to capture the dominant dynamics up to a desired bandwidth.

The model mismatch between the low order model $P_0$ and the $i^{\text {th }}$ experimental response $P_i$ can be quantified by the relative error $E_i:=\left|\frac{P_i-P_0}{P_0}\right|(i=1, \ldots, N)$. The right side of Figure 3 shows this relative error $E_i$ vs. frequency for all $N$ systems (blue). At low frequencies the relative error is roughly $\leq-40 \mathrm{db}=0.01$, i.e. all experimental data are within $\approx 1 \%$ of the design model. For frequencies $\geq 3.0$ the largest relative error exceeds $0 \mathrm{db}=1.0$. Thus at least some experimental responses have more than $100 \%$ error at high frequencies.
This motivates the definition of the following set of dynamic models:
$$
\mathcal{M}_B:=\left\{\tilde{P} \text { LTI }:\left|\frac{\tilde{P}(j \omega)-P_0(j \omega)}{P_0(j \omega)}\right| \leq B(j \omega) , \forall \omega\right\}
$$
where $B$ is the frequency-dependent bound on the relative error. Suppose the bound is selected to be the largest error among all the responses: $B(j \omega):=\max _i E_i(j \omega)$. In this case, $\mathcal{M}_B$ contains the low-order model $P_0$ and each of the experimental responses $P_i$ for $i=1, \ldots, N$.

In general, $\mathcal{M}_B$ captures dynamic uncertainty with a given nominal model $P_0$ and error bound $B$. Typically $B$ is small $(\ll 1)$ at low frequencies and rising above 1 at high frequencies. This captures the accuracy of the nominal model at low frequencies (long time scales) with loss of fidelity at high frequencies (short time scales). The state dimension of $\tilde{P} \in \mathcal{M}_B$ is unspecified and thus $\mathcal{M}_B$ captures unmodeled (neglected) dynamics of arbitrary order. This is a powerful uncertainty modeling concept as neglected dynamics are often a key issue.

A related, normalized description for this uncertainty set is defined by a nominal model $P_0$ and LTI "weight" $W$ as follows:
$$
\mathcal{M}_W:=\left\{\tilde{P}:=P_0(1+W \Delta): \Delta \text { LTI, stable },\|\Delta\|_{\infty} \leq 1\right\}
$$
Any $\tilde{P} \in \mathcal{M}_W$ satisfies $\left|\frac{\tilde{P}-P_0}{P_0}\right| \leq|W|$. Thus $|W(j \omega)|$ is a bound on the relative error at all frequencies. The relative error bound is unaffected by the phase of $W$ and hence $W$ may be chosen, without loss of generality, to be stable and minimum phase. It can also be chosen as a transfer function or state-space model for numerical calculations. The normalized uncertainty $\Delta$ is an LTI, stable system with gain bounded by 1 at all frequencies. The assumption that $\Delta$ is stable implies that $\tilde{P}$ can only have RHP poles at the same locations as $P_0$. More advanced dynamic uncertainty models allow for variations in RHP poles as discussed in Section 4. The uncertainty set $\mathcal{M}_W$ in Equation 5 is referred to as a multiplicative uncertainty model. Other variations exist, e.g. an additive uncertainty model $\tilde{P}=P_0+W \Delta$.

Example 3. The Matlab command ultidyn can be used to construct dynamic, LTI uncertainty. The following snippet of code constructs an system with $5 \%$ uncertainty at low frequencies, $100 \%$ uncertainty at $5 \mathrm{rad} / \mathrm{sec}$, and $200 \%$ uncertainty at high frequencies.

	 P0 = tf(1,[1 1]);                     % Nominal Plant
	 W = makeweight(0.05,5,2);     % Uncertainty Weight
	 Delta = ultidyn(’Delta’,[1 1]);   % Scalar, normalized uncertainty
	 Ptil = P0*(1+W*Delta);          % Model with multiplicative uncert.