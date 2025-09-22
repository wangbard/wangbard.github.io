---
layout: post
title: "Degree Reduction"
permalink: /private/degree_reduction/
date: 2025-09-22 23:56:00 +0200
math: true
---


- **Goal:** compute a multiplication gate on shares
- **Setup:**
	- $a$ is t-shared via $A(x)$ , $b$ is t-shared via $B(x)$
	- Want each party to hold a t-share of $ab$
- **Naïve idea:** compute $A(\alpha_i)B(\alpha_i)$
	- Problem 1: product is degree $2t$
	- Problem 2: polynomial not random (factorable into $A,B$ ; a fresh random sharing shouldn’t reveal such structure)
- **Fix: degree reduction**
	- The degree- $2t$ product polynomial $C(x)$ is uniquely determined if $n>2t$
	- Interpolate:
  
	  $$
      C(x) = \sum_{i=1}^n C(\alpha_i)\,\ell_i(x),\quad \ell_i(x)=\prod_{j\ne i}\frac{x-\alpha_j}{\alpha_i-\alpha_j}
	  $$
- **But! We only need the secret:**

  $$
  C(0) = \sum_{i=1}^n \lambda_i\,C(\alpha_i),\quad \lambda_i=\ell_i(0)
  $$

  where $\lambda_i$ is a constant.  
  This becomes a **linear relation**, and we know how to deal with linear relations.  

- **Trick (reshare + recombine):**
	- Each party $i$ (who knows $C(\alpha_i)$ ) **t-shares** $C(\alpha_i)$ with fresh randomness
	- Everyone linearly combines these t-shares using the public weights $\lambda_i$
	- Result: a fresh **t-sharing of (C(0)=ab)**
- **Intuition recap:**
	- Multiplication → degree blow-up
	- Interpolation focuses only on the constant term
	- Identify that the problem becomes a linear relation
	- Resharing restores randomness
	- Weighted recombination yields a valid t-share of the product
