---
title: "Phase Kickback and Ancilla Qubits"
description: In this article, we investigate different choice of ancilla qubits for phase kickback in different quantum algorithms, particularly in Quantum Phase Estimation, Deutsch-Josza and Grover's Algorithm.
date: 2024-09-07 15:00:00 +0800
categories: [Quantum Computing, Quantum Algorithm]
tags: [quantum computing, quantum algorithm]     # TAG names should always be lowercase
math: true
---

## **1. Why Different Starting States for Ancilla Qubit in Phase Kickback?**

In quantum algorithms, the **ancilla qubit** plays a central role in the **phase kickback** mechanism, which is essential for transferring phase information. Depending on the algorithm, the ancilla qubit is initialized in different states, either $\ket{0}$, $\ket{1}$, or an eigenstate $\ket{u}$ of a unitary operator. These choices reflect the goals of each algorithm, whether accumulating phase information or inducing a phase flip.

For example, in **Quantum Phase Estimation (QPE)**, the ancilla qubit starts in an eigenstate of the unitary operator to extract phase information. In contrast, algorithms like **Deutsch-Josza** and **Grover’s Algorithm** use the ancilla qubit to apply a phase flip, and thus it is initialized in the state $\ket{1}$.

This paper explores the different roles and starting states of the ancilla qubit in these algorithms, focusing on **Quantum Phase Estimation** and **Deutsch-Josza and Grover’s Algorithm**.

## **2. Quantum Phase Estimation (QPE)**

**Quantum Phase Estimation (QPE)** is designed to estimate the phase (an eigenvalue) associated with a unitary operator $U$, when applied to its eigenstate $\ket{u}$. The **ancilla qubit** in QPE plays a passive role in phase kickback, holding the eigenstate information that is transferred to the control qubits.

### **2.1 Phase Kickback in QPE**

In QPE, the ancilla qubit is not initialized in the usual computational basis states ($\ket{0}$ or $\ket{1}$), but rather in an eigenstate $\ket{u}$ of the unitary operator $U$. This choice is crucial because the goal of QPE is to accumulate phase information about $U$ by interacting with its eigenstate.

- **Controlled Unitary Application:**
    - The control qubits (which start in $\ket{0}^{\otimes n}$ and are placed into superposition by Hadamard gates) control the application of the unitary $U$ to the ancilla qubit.
    - The unitary operator $U$ acts on the ancilla qubit, which is initialized in the eigenstate $\ket{u}$, yielding:
    
    $$
    U \ket{u} = e^{2\pi i \phi} \ket{u}.
    $$
    
    - The phase $e^{2\pi i \phi}$ is kicked back onto the control qubits through this controlled operation, transferring the phase information from the ancilla qubit to the control qubits.
    
- **Phase Kickback:**
    - After the controlled operation, the phase information $e^{2\pi i \phi}$ is transferred to the control qubits, creating a superposition state:
    
    $$
    \frac{1}{\sqrt{2}} \left( \ket{0} + e^{2\pi i \phi} \ket{1} \right).
    $$
    
    - The ancilla qubit remains in the eigenstate $\ket{u}$, while the phase is now encoded in the control qubits.
    
- **Quantum Fourier Transform (QFT):**
    - The control qubits, now holding the phase information, undergo a **quantum Fourier transform (QFT)** to extract the phase $\phi$.

In summary, in QPE, the ancilla qubit is initialized in an eigenstate to facilitate the transfer of phase information to the control qubits, and the ancilla qubit itself remains unchanged in the process.

## **3. Deutsch-Josza and Grover’s Algorithm**

In contrast to QPE, the **ancilla qubit** in algorithms like **Deutsch-Josza** and **Grover’s Algorithm** plays an active role by introducing a **phase flip** through phase kickback. In both algorithms, the ancilla qubit is initialized in the state $\ket{1}$, allowing for the extraction of information based on the function $f(x)$. A key distinction between these algorithms and QPE is that, instead of using a controlled unitary as in QPE, these algorithms use a **CNOT gate** to apply phase kickback and induce the phase flip. The CNOT gate interacts with the ancilla qubit, flipping its phase when the function $f(x)$ evaluates to 1.  

In both algorithms, the process follows these steps:

- The system starts by applying Hadamard gates to place the qubits in an equal superposition of all possible input states.
- The oracle, represented by a function $f(x)$, applies a **CNOT gate** to the ancilla qubit to induce a phase flip if $f(x) = 1$. If $f(x) = 0$, no phase flip occurs.
- The phase flip changes the sign of the ancilla qubit’s state, introducing quantum interference effects that help identify the solution or the balanced function.

### **3.1 Phase Kickback in Deutsch-Josza and Grover’s**

In both the Deutsch-Josza and Grover’s algorithms, the ancilla qubit is initialized in $\ket{1}$ to facilitate phase kickback. This initialization ensures that a phase flip can be induced if the function $f(x)$ evaluates to 1, marking the relevant states for measurement. The CNOT gate is used to induce the phase flip, interacting with the ancilla qubit when the function evaluates to $f(x) = 1$.

Here’s a more detailed explanation of how the phase flip works:

- Initially, the ancilla qubit is in the $\ket{1}$ state, and the system is described by the state $\ket{\psi_0}$:
  
    $$
    \ket{\psi_0} = \ket{x} \otimes \ket{1}
    $$

- After applying a Hadamard gate to the ancilla qubit, it enters a superposition state:
  
    $$
    \ket{\psi_1} = \ket{x} \otimes \frac{1}{\sqrt{2}} (\ket{0} - \ket{1})
    $$

- When the CNOT gate is applied, it acts on the system based on the value of the function $f(x)$:
    - **If $f(x) = 0$**: The CNOT gate does not induce a phase flip, and the ancilla qubit remains in the superposition state without any sign change:
      
        $$
        \ket{\psi_2} = \ket{x} \otimes \frac{1}{\sqrt{2}} (\ket{0} - \ket{1})
        $$

    - **If $f(x) = 1$**: The CNOT gate flips the phase of the ancilla qubit, resulting in a sign change. This leads to the following state:
      
        $$
        \ket{\psi_2} = \ket{x} \otimes \frac{1}{\sqrt{2}} (-1)^{f(x)}( \ket{0} - \ket{1}) = (-1)^{f(x)} \ket{x} \otimes \frac{1}{\sqrt{2}} (\ket{0} - \ket{1})
        $$

- Finally, after the function evaluation, the resulting state is:
  
    $$
    \ket{\psi_3} = (-1)^{f(x)} \ket{x} \otimes \ket{1}
    $$

Here, the phase flip ensures that the marked state (for which $f(x) = 1$) has its sign flipped, which is critical for later amplification and interference effects.

### **3.2 How Phase Kickback is Used in Each Algorithm**

- **In the Deutsch-Josza algorithm**:
    - After the Hadamard gates create the superposition of all input states, the oracle uses the CNOT gate to apply phase flips to the states where $f(x) = 1$. After querying the oracle, another round of Hadamard gates is applied to interfere with the states, and a final measurement is made to determine whether the function is constant or balanced.
    
    - **Constant function**: If the function is constant (i.e., $f(x) = 0$ or $f(x) = 1$ for all inputs), the qubits will collapse into the **all-zero state** $\ket{00\ldots0}$. In this case, the phase flip contributes only to a global phase, which does not affect the measurement outcome, as it introduces no relative phase differences between the qubits. Since global phases are unobservable in quantum measurements, the system’s behavior remains unchanged, and the measurement will yield the all-zero state.

    - **Balanced function**: If the function is balanced, the oracle applies phase flips to the states where $f(x) = 1$. These phase flips introduce destructive interference between the states. After applying the final Hadamard transformation, this interference causes certain computational paths to cancel out, resulting in zero probability of the qubits collapsing into the $\ket{00\ldots0}$ state. Therefore, when the measurement is made, the system will collapse into a state different from $\ket{00\ldots0}$, indicating that the function is balanced.

- **In Grover’s algorithm**:
    - Grover’s algorithm works by repeatedly applying two main steps: the **oracle** (which uses the CNOT gate for a phase flip) and the **diffusion operator** (for amplitude amplification). The oracle uses the CNOT gate to flip the sign of the marked state's amplitude if $f(x) = 1$, and leaves the unmarked states unchanged if $f(x) = 0$.
    
    - After the phase flip by the oracle, the **diffusion operator** is applied. This operator (comprising Hadamard gates, X gates, and a multi-controlled Z gate) inverts the amplitudes of all states about their average. This process amplifies the marked state's amplitude while reducing the amplitudes of the other states.
    
    - With each iteration, the amplitude of the marked state increases, making it more likely to be measured as the correct solution. After a few iterations, the probability of finding the correct solution becomes significantly higher, and a final measurement will yield the solution with high probability.

## **4. Summary**

The starting state of the **ancilla qubit** in phase kickback depends on the purpose of the algorithm:

- In **Quantum Phase Estimation (QPE)**, the ancilla qubit starts in the eigenstate $\ket{u}$ of the unitary operator $U$ to facilitate the accumulation of phase information.
- In **Deutsch-Josza and Grover’s Algorithm**, the ancilla qubit starts in $\ket{1}$ to induce a phase flip based on the function $f(x)$, which is essential for leveraging quantum interference or marking the correct solution.
