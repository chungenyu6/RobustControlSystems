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

This section reviews several useful facts regarding transformations of complex numbers. There are three basic transformations
- Translation/Shift: Let $c \in \mathbb{C}$ be given. Consider the function $f: \mathbb{C} \rightarrow \mathbb{C}$ defined by $f(z):=z+c$. This corresponds to translating a complex number $z$ to $z+c$. This translation maps $\operatorname{Disk}\left(I_L, I_R\right)$ to $\operatorname{Disk}\left(I_L+c, I_R+c\right)$.
- Inversion: Consider the function $f: \mathbb{C} \rightarrow \mathbb{C}$ defined by $f(z):=\frac{1}{z}$. If $I_L>0$ then $\operatorname{Disk}\left(I_L, I_R\right)$ is in the right half plane. Similarly, if $I_R<0$ then Disk $\left(I_L, I_R\right)$ is in the left half plane. Thus if either $I_L>0$ or $I_R<0$ then $\operatorname{Disk}\left(I_L, I_R\right)$ does not contain $z=0$. In such cases the inversion is well-defined mapping $\operatorname{Disk}\left(I_L, I_R\right)$ to $\operatorname{Disk}\left(\frac{1}{I_R}, \frac{1}{I_L}\right)$.
- Scaling/Rotation: Let $c \in \mathbb{C}$ be given. Consider the function $f: \mathbb{C} \rightarrow \mathbb{C}$ defined by $f(z):=c z$. In general this multiplication corresponds to a scaling by $|c|$ and a rotation by $\angle c$. If $c \in \mathbb{R}$ then this multiplication corresponds to a pure scaling. Specifically, if $c>0$ then $c z$ maps $\operatorname{Disk}\left(I_L, I_R\right)$ to $\operatorname{Disk}\left(c I_L, c I_R\right)$. Similarly, if $c<0$ then $c z$ maps $\operatorname{Disk}\left(I_L, I_R\right)$ to $\operatorname{Disk}\left(c I_R, c I_L\right)$.
- Linear Fractional (or Möbius) Transformation: Consider the function $f: \mathbb{C} \rightarrow \mathbb{C}$ defined by $f(z):=\frac{a z+b}{c z+d}$ where $a, b, c, d \in \mathbb{C}$ and $a d-b c \neq 0$. This is called a linear fractional transformation (LFT) or Möbius transformation. An LFT can be decomposed in a sequence of translation, inversion, and scaling/rotation transformations. LFTs map lines and circles in the complex plane into lines and circles. Specific examples are given below.

---
## Ex
Example 8. Let $m \in[0,1)$ be given. The transformation $f(z)=1+m z$ corresponds to a scaling by $m$ and translation by 1 . This transformation maps the unit disk, i.e. Disk $(-1,1)$, to $\operatorname{Disk}(1-m, 1+m)$. As $m \rightarrow 1$, the transformed disk approaches $\operatorname{Disk}(0,2)$.

Example 9. Let $m \in[0,1)$ be given and consider the transformation $f(z)=\frac{1}{1-m z}$. This corresponds to a sequence of three operations: (i) Scaling by $-m$, (ii) Translation by 1 , and (iii) Inversion. The effect of $f$ on the unit disk, i.e. $\operatorname{Disk}(-1,1)$, is obtained by following this sequence of operations. The first two operations maps the unit disk to Disk $(1-m, 1+m)$. The third operation then maps to $\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$. Thus the transformation $f$ maps $\operatorname{Disk}(-1,1)$ to $\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$. As $m \rightarrow 1$, the transformed disk approaches $\{w \in \mathbb{C}: \operatorname{Re}\{w\} \geq 0.5\}$. 

Example 10. Let $m \in[0,1)$ be given and consider the transformation $f(z)=\frac{1+m z}{1-m z}$. This can be equivalently written as $f(z)=-1+\frac{2}{1-m z}$. In this form, $f$ corresponds to three operations:
(i) Map $z$ to $\frac{1}{1-m z}$, (ii) Scale by 2, and (iii) Translate by -1 . The previous example showed that the first operation maps $\operatorname{Disk}(-1,1)$ to $\operatorname{Disk}\left(\frac{1}{1+m}, \frac{1}{1-m}\right)$. The next two operations map to $\operatorname{Disk}\left(-1+\frac{2}{1+m},-1+\frac{2}{1-m}\right)=\operatorname{Disk}\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$. Thus $f$ maps Disk $(-1,1)$ to Disk $\left(\frac{1-m}{1+m}, \frac{1+m}{1-m}\right)$. As $m \rightarrow 1$, the transformed disk approaches $\{w \in \mathbb{C}: \operatorname{Re}\{w\} \geq 0\}$.
