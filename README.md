# QuantumGaltonBoard
Monte Carlo Simulation via Quantum Circuits - THE WISER Program 2025 Project

## Project Details
- **Project Name :** Quantum Walks and Monte Carlo
- **Team Name :** SeeQ
- **Team Members:**
  - Raouf Ould Ali | gst-TFh9DYIlGTGankG
  - Rassim Cherir | gst-izEWAXhadEwOt1j

## Project Summary
We set out to build a **Quantum Galton Board (QGB)** as part of the WISER 2025 Quantum Program, aiming to create a *universal statistical simulator* that works like a classical Galton board but with a quantum twist. The classical version drops a ball through pegs, each deflecting it left or right with equal probability, producing a Gaussian distribution. In quantum computing, we can do better — **superposition** lets us explore all possible paths at once, and measurement picks one outcome at the end.

In **Task 1**, we focused on theory and literature. We studied how the binomial distribution $\frac{1}{2^n} \binom{n}{k}$ emerges classically and explored quantum walk ideas from recent research. The takeaway: the Galton board is a perfect model for testing quantum Monte Carlo methods, with clear visual and mathematical parallels.

In **Task 2**, we implemented the general QGB algorithm. We started with a single peg:

1. Prepare the “ball” with an `X` gate.
2. Apply a **Hadamard** on a control qubit to create equal superposition.
3. Use `CSWAP` and `CNOT` gates to send the ball left or right.

Measuring at the end reproduces the classical 50–50 split. For an n-level board, we chained these peg blocks into levels, resetting the control qubit between levels so each row acts independently. We found the resource cost to be $2n + 2$ qubits, $O(n^2)$ gates, and linear circuit depth. The code was built modularly, making it scalable and reusable.

By then we had a working **Gaussian-producing QGB**, but in **Task 3** we wanted variety. We created two new versions:

* **Exponential QGB** — We added SWAP gates to bias the ball toward one edge, producing an asymmetric, exponential-like probability distribution.
* **Hadamard Walk QGB** — We skipped control-qubit resets, preserving quantum coherence across levels. This let interference effects emerge, creating a non-classical distribution similar to a quantum walk.

Testing was done in Qiskit’s AerSimulator with 1024 shots, up to 8 levels. The Gaussian QGB matched the expected binomial curve almost perfectly, while the exponential and Hadamard walk versions showed the predicted asymmetry and interference patterns. The results confirmed our architecture could generate not just the standard symmetric distribution, but also biased and quantum-interference-driven ones.

By completing Tasks 1–3, we delivered:

* A solid theoretical foundation for quantum statistical simulation.
* A scalable, verified algorithm for an n-level QGB.
* Three distinct distributions — Gaussian, exponential, and quantum-walk-style — all from the same modular design.

This work shows how quantum circuits can model rich statistical behaviors beyond the classical limit, and it lays the groundwork for future tasks like noise modeling, error mitigation, and exploring quantum advantage in real-world Monte Carlo problems.


## Project Deliverables
- [2-pages summary of the litterature](https://github.com/SpeedCode210/QuantumGaltonBoard/blob/main/summary.pdf)
- [Implementation Notebook](https://github.com/SpeedCode210/QuantumGaltonBoard/blob/main/QGB.ipynb)
- [Presentation Deck](https://github.com/SpeedCode210/QuantumGaltonBoard/blob/main/presentation.pdf)
