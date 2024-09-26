---
title: "The Heisenberg Uncertainty Principle"
date: 2024-09-26 21:27:00 +0800
categories: [Quantum Computing]
tags: [quantum computing, math]     # TAG names should always be lowercase
math: true
---

## **Introduction**

The Heisenberg uncertainty principle is one of the foundational results in quantum mechanics. It establishes that there are limits to the precision with which certain pairs of physical properties, such as position and momentum, can be simultaneously known. 

When I first encountered the explanation of the uncertainty principle in Box 2.4 of Section 2.2.5 in Nielsen & Chuang's **Quantum Computation and Quantum Information**[^1], I found it somewhat confusing. To provide some clarification, I aim to write down these explanations for my own future reference and for those who may find the derivation in the textbook equally confusing. In this article, I will walk through the detailed steps involved in deriving the uncertainty principle.

## **Derivation**

We begin with two Hermitian operators $$ A $$ and $$ B $$, and let $$ \ket{\psi} $$ be a quantum state. Consider the expectation value of the product $$ A B $$ in the state $$ \ket{\psi} $$, which can be expressed as a complex number:

$$
\bra{\psi} A B \ket{\psi} = x + iy,
$$

where $$ x $$ and $$ y $$ are real numbers. Although the expectation value of a single Hermitian operator is always real, the expectation value of the product of two Hermitian operators $$ A $$ and $$ B $$ can be complex. This is because the product $$ AB $$ is generally not Hermitian, meaning $$ (AB)^\dagger = B A \neq AB $$, allowing for a complex expectation value.

We will now examine the interactions between the two operators $$ A $$ and $$ B $$ by considering their **commutator** $$ [A, B] $$ and **anticommutator** $$ \{A, B\} $$, which are defined as:

$$
[A, B] = A B - B A, \quad \{A, B\} = A B + B A.
$$

Using the fact that $$ \bra{\psi} A B \ket{\psi} = x + iy $$, the expectation value of the commutator is:

$$
\bra{\psi} [A, B] \ket{\psi} = \bra{\psi} (A B - B A) \ket{\psi} = \bra{\psi} A B \ket{\psi} -\bra{\psi} (AB)^\dagger \ket{\psi} = 2iy.
$$

Since $$ \bra{\psi} (A B)^\dagger \ket{\psi} = (\bra{\psi} A B \ket{\psi})^* $$, we can move the dagger outside the inner product, taking the complex conjugate of the expectation value. Thus, subtracting $$ \bra{\psi} (A B)^\dagger \ket{\psi} = x - iy $$ from $$ \bra{\psi} A B \ket{\psi} = x + iy $$ results in $$ 2iy $$. Similarly, the expectation value of the anticommutator is:

$$
\bra{\psi} \{A, B\} \ket{\psi} = \bra{\psi} (A B + B A) \ket{\psi} = \bra{\psi} A B \ket{\psi} + \bra{\psi} (A B)^\dagger \ket{\psi} = 2x.
$$

Since $ \|\bra{\psi} AB \ket{\psi}\|^2 = x^2 + y^2 $, it directly leads to the conclusion that: 

$$
\begin{equation}
|\bra{\psi} [A, B] \ket{\psi}|^2 + |\bra{\psi} \{A, B\} \ket{\psi}|^2 = 4|\bra{\psi} AB \ket{\psi}|^2.
\label{eq:1}
\end{equation}
$$

Next, we apply the **Cauchy-Schwarz inequality**. In bra-ket notation, this inequality states that:

$$
\begin{equation}
    |\bra{\psi} AB \ket{\psi}|^2 \leq \bra{\psi} A^2 \ket{\psi} \bra{\psi} B^2 \ket{\psi}.
    \label{eq:2}
\end{equation}
$$

This tells us that the square of the expectation value of $$ AB $$ is bounded by the product of the expectation values of $$ A^2 $$ and $$ B^2 $$. To understand this better, we can refer to the standard form of the Cauchy-Schwarz inequality for inner products:

$$
|\braket{u, v}|^2 \leq \braket{u, u} \cdot \braket{v, v},
$$

where $$ u $$ and $$ v $$ are vectors in an inner product space. The quantum mechanical version of this inequality is a direct application of the same principle.

By combining Equation \eqref{eq:1} with the result from Equation \eqref{eq:2}, we derive the following bound on the expectation value of the commutator:

$$
|\bra{\psi} [A, B] \ket{\psi}|^2 \leq 4 \bra{\psi} A^2 \ket{\psi} \bra{\psi} B^2 \ket{\psi}.
$$

At this point, we substitute the operators $$ A = C - \langle C \rangle $$ and $$ B = D - \langle D \rangle $$, where $$ \langle C \rangle = \bra{\psi} C \ket{\psi} $$ and $$ \langle D \rangle = \bra{\psi} D \ket{\psi} $$ are the expectation values of the observables $$ C $$ and $$ D $$. 

Here, $$ C - \langle C \rangle $$ represents the deviation of the operator $$ C $$ from its expected value, which measures how much the observable fluctuates around its mean. The subtraction is interpreted as $$ C - \langle C \rangle I $$, where $$ I $$ is the identity matrix.

Since the expectation values $$ \langle C \rangle $$ and $$ \langle D \rangle $$ are scalars, they commute with all operators, meaning subtracting them does not affect the commutator:

$$
[C - \langle C \rangle, D - \langle D \rangle] = [C, D].
$$

After the substitution, we arrive at the following inequality:

$$
\begin{equation}
    |\bra{\psi} [C, D] \ket{\psi}|^2 \leq 4 \Delta(C)^2 \Delta(D)^2,
    \label{eq:3}
\end{equation}
$$

where $$ \Delta(C) $$ and $$ \Delta(D) $$ are the standard deviations (or uncertainties) in measuring $$ C $$ and $$ D $$, defined as:

$$
\Delta(C)^2 = \bra{\psi} (C - \langle C \rangle)^2 \ket{\psi}, \quad \Delta(D)^2 = \bra{\psi} (D - \langle D \rangle)^2 \ket{\psi}.
$$

Since $$ C - \langle C \rangle $$ is Hermitian, $$ (C - \langle C \rangle)^\dagger = C - \langle C \rangle $$. We can prove that $$ (C - \langle C \rangle)^2 $$ is **positive semi-definite**. Let $$ \ket{\psi} $$ be any state. Then, we consider the expectation value of $$ (C - \langle C \rangle)^2 $$ in the state $$ \ket{\psi} $$:

$$
\bra{\psi} (C - \langle C \rangle)^2 \ket{\psi} = \bra{\psi} (C - \langle C \rangle)^\dagger (C - \langle C \rangle) \ket{\psi} = \|(C - \langle C \rangle) \ket{\psi}\|^2 \geq 0
$$

This positivity allows us to take the square root of both sides of Equation \eqref{eq:3} securely, leading to the expression of the Heisenberg uncertainty principle:

$$
\begin{equation}
    \Delta(C) \Delta(D) \geq \frac{|\bra{\psi} [C, D] \ket{\psi}|}{2}.
    \label{eq:4}
\end{equation}
$$

This inequality expresses the fundamental limit on the precision with which the observables $$ C $$ and $$ D $$ can be simultaneously measured.

## **Example: Pauli Operators $$ X $$ and $$ Y $$**

As an example, consider the Pauli matrices $$ X $$, $$ Y $$, and $$ Z $$. From their commutation relations, we know:

$$
[X, Y] = 2iZ.
$$

For the quantum state $$ \ket{0} $$, which is an eigenstate of the Pauli-$$ Z $$ matrix, we have:

$$
Z \ket{0} = \ket{0}.
$$

Taking the expectation value of $$ Z $$ in this state gives:

$$
\bra{0} Z \ket{0} = 1.
$$

Thus, the uncertainty principle \eqref{eq:4} for the Pauli operators $$ X $$ and $$ Y $$ becomes:

$$
\Delta(X) \Delta(Y) \geq \frac{|\bra{0} [X, Y] \ket{0}|}{2} = \frac{|\bra{0} 2iZ \ket{0}|}{2} = \frac{2}{2} = 1.
$$

This shows that the product of the uncertainties in measuring $$ X $$ and $$ Y $$ in the state $$ \ket{0} $$ must be at least 1. As a result, neither $$ \Delta(X) $$ nor $$ \Delta(Y) $$ can be zero. 

More generally, for any pair of non-commuting observables (i.e., $$ [A, B] \neq 0 $$), the uncertainty principle imposes a positive lower bound on the product of their uncertainties. If the uncertainty in one observable were to drop to zero, the inequality could not be satisfied, as the product would also be zero, violating the bound. Moreover, this implies that reducing the uncertainty in one observable forces the uncertainty in the other to increase, ensuring that some uncertainty always remains. This reflects a fundamental limit in quantum mechanics when measuring non-commuting observables.

## **Reference** 

[^1]: Nielsen, Michael A.; Chuang, Isaac L. (2010-12-09). [Quantum Computation and Quantum Information](https://books.google.com.hk/books?id=j2ULnwEACAAJ&redir_esc=y)
