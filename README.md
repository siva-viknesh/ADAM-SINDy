# ADAM-SINDy  
**An Efficient Optimization Framework for Parameterized Nonlinear Dynamical System Identification**

📄 Paper: https://doi.org/10.1103/dwkk-5g2h  
📊 Journal: *Physical Review Research (2026)*  

---

## 🔍 Overview

**ADAM-SINDy** is a differentiable optimization framework for discovering governing equations of nonlinear dynamical systems directly from data.

It extends the classical **SINDy (Sparse Identification of Nonlinear Dynamics)** method by enabling:

- Simultaneous optimization of nonlinear parameters and coefficients  
- Reduced dependence on predefined candidate libraries  
- Improved robustness and accuracy in complex systems  

Unlike classical SINDy, which requires prior knowledge of nonlinear parameters (e.g., frequencies, exponents), ADAM-SINDy learns them directly from data using gradient-based optimization (ADAM).

---

## ⚡ Key Contributions

- Differentiable SINDy framework using ADAM optimizer  
- Joint optimization of:
  - Coefficients  
  - Nonlinear parameters (e.g., Fourier frequencies, exponents)  
  - Sparsity controls  
- Adaptive sparsity (candidate-wise weighting) inspired by IRLS  
- Physics-informed extensions via differential equation-based loss  
- Machine-precision recovery of governing equations  

---

## 🧠 Why ADAM-SINDy?

| Method | Strength | Limitation |
|--------|----------|------------|
| SINDy | Fast, interpretable | Needs predefined nonlinear parameters |
| Symbolic Regression | Flexible | Computationally expensive, unstable |
| **ADAM-SINDy** | Combines both | Slightly higher optimization cost |

ADAM-SINDy bridges sparsity, flexibility, and gradient-based learning.

---

## 🧪 Benchmark Problems

- Harmonic oscillator (unknown frequency)  
- Van der Pol oscillator (fractional exponent)  
- ABC flow (multi-frequency chaotic system)  
- Chemical reaction kinetics (exponential parameters)  
- Pharmacokinetics (time-dependent nonlinearities)  
- Wildfire PDE (spatiotemporal dynamics)  

ADAM-SINDy consistently recovers correct governing equations while maintaining sparsity.

---

## 🏗️ Method Summary

We solve:

\[
\dot{X} = \Theta(X; \theta)\,\Xi
\]

where:
- \( \Theta(X; \theta) \): candidate library with trainable nonlinear parameters  
- \( \Xi \): sparse coefficients  

### Optimization

\[
\min_{\Xi, \theta, \Gamma} \; \| \dot{X} - \Theta(X; \theta)\Xi \|_2^2 + \lambda \| |\Gamma|\Xi \|_1
\]

- All parameters are optimized jointly  
- Implemented in PyTorch using ADAM  

---

## 🧰 Features

- End-to-end differentiable pipeline  
- No need to predefine nonlinear parameters  
- Adaptive sparsity tuning  
- Physics-informed loss support  
- Works for ODEs and PDEs  

---

## 🧩 Applications

- Physics-informed modeling  
- Fluid dynamics  
- Chemical kinetics  
- Biological systems  
- Control and system identification  

---

## 📚 Citation

```bibtex
@article{viknesh2026adam_sindy,
  title={ADAM-SINDy: An efficient optimization framework for parameterized nonlinear dynamical system identification},
  author={Viknesh, Siva and Tatari, Younes and Christenson, Chase and Arzani, Amirhossein},
  journal={Physical Review Research},
  year={2026},
  doi={10.1103/dwkk-5g2h}
}
```
