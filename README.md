<h2 align="center">⚙️ ADAM-SINDy: An Efficient Optimization Framework for Parameterized Nonlinear Dynamical System Identification</h2>

<p align="center">
  <a href="https://doi.org/10.1103/dwkk-5g2h"><img src="https://img.shields.io/badge/Phys.Rev.Research-013040-blue.svg" alt="Journal"></a>
  <a href="https://github.com/siva-viknesh/ADAM-SINDy"><img src="https://img.shields.io/badge/GitHub-ADAM--SINDy-blue?logo=github" alt="GitHub"></a>
  <img src="https://img.shields.io/badge/PyTorch-Framework-orange?logo=pytorch" alt="PyTorch">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License">
</p>

**ADAM-SINDy** is a differentiable optimization framework within the SINDy paradigm for identifying parameterized nonlinear dynamical systems directly from data. By employing the **ADAM optimizer**, it simultaneously identifies sparse governing equations *and* the nonlinear parameters embedded within candidate library functions — such as trigonometric frequencies, exponential bandwidths, or polynomial exponents — without requiring any prior knowledge of these characteristics.

---

## ✨ Key Contributions

- 🎯 **Simultaneous Optimization of Nonlinear Parameters and Coefficients**  
  Jointly optimizes both the sparse linear coefficients **ξ** and the nonlinear parameters **α** embedded in the candidate library `Θ(x; α)` using ADAM in a single differentiable pass — no need for a hand-crafted or pre-fixed dictionary.

- 🔍 **No Prior Knowledge Required**  
  Identifies unknown nonlinear characteristics (e.g., frequency in `sin(αx)`, bandwidth in `exp(αx²)`, exponents in `xᵅ`) directly from observational data, dramatically broadening the scope of identifiable systems.

- 📉 **Reduced Library Sensitivity**  
  Integrated global optimization dynamically adapts candidate functions to the data, reducing the sensitivity to the initial library choice that hampers traditional SINDy approaches.

- 🌐 **Broad Applicability**  
  Demonstrated across coupled nonlinear ODEs (oscillators, chaotic flows, reaction and pharmacokinetics) and nonlinear PDEs (wildfire transport), establishing both accuracy and generality.

---

## 🏗️ Framework Overview

```
Observed Time-Series Data:  x(t)
              │
     ┌────────▼────────────────────┐
     │  Numerical Differentiation  │   Finite differences / total variation
     │  ẋ ≈ dx/dt                  │   regularization for derivative estimation
     └────────┬────────────────────┘
              │
     ┌────────▼────────────────────┐
     │  Parameterized Library      │   Θ(x; α) — candidate functions with
     │  Construction               │   trainable nonlinear parameters α
     └────────┬────────────────────┘
              │                             ┌─────────────────────────┐
     ┌────────▼────────────────────┐        │  Nonlinear Parameters α  │
     │  ADAM Optimization Loop     │◄───────│  (frequencies, exponents,│
     │                             │        │   bandwidths, etc.)       │
     │   min  ‖ẋ − Θ(x;α)·ξ‖²    │        └─────────────────────────┘
     │    α,ξ  + λ‖ξ‖₁            │◄───────┌─────────────────────────┐
     └────────┬────────────────────┘        │  Sparse Coefficients ξ  │
              │                             └─────────────────────────┘
     ┌────────▼────────────────────┐
     │  Sparsification             │   Sequential thresholding to enforce
     │  (STLSQ / hard threshold)   │   parsimonious model structure
     └────────┬────────────────────┘
              │
     ┌────────▼────────────────────┐
     │  Identified Governing       │   ẋ = f(x; α*, ξ*)
     │  Equations                  │   Interpretable, sparse, parameterized
     └─────────────────────────────┘
```

---

## 🔬 Benchmark Systems

ADAM-SINDy is validated across a broad spectrum of dynamical systems:

| Category | System | Nonlinear Parameter |
|---|---|---|
| **Nonlinear Oscillators** | Duffing, Van der Pol, coupled oscillators | Polynomial exponents, frequency |
| **Chaotic Fluid Flows** | Lorenz system, chaotic ODE models | Nonlinear coupling terms |
| **Reaction Kinetics** | Nonlinear chemical reaction networks | Reaction rate exponents |
| **Pharmacokinetics** | Drug absorption and elimination dynamics | Exponential bandwidths |
| **Nonlinear PDEs** | Wildfire convection–diffusion–reaction transport | Nonlinear source term parameters |

---

## 📈 Results Highlights

- ADAM-SINDy achieves **significant improvements** over classical SINDy and symbolic regression on all parameterized benchmark systems, particularly when nonlinear parameters are unknown.
- Demonstrates that **concurrent optimization of all parameters** — rather than sequential or fixed-library approaches — is critical for accurate identification of nonlinear systems.
- Reduces the sensitivity of discovered equations to the initial choice of candidate library, enabling robust identification even from **sparse or noisy observational data**.
- Successfully identifies governing equations for both **low-dimensional ODEs** and **high-dimensional nonlinear PDE systems**, establishing methodological generality.

---

## 🔭 Future Directions

- **Stochastic and noisy systems** — robust identification under high noise via probabilistic extensions
- **Partial observations** — identification from incomplete state measurements
- **Autonomous PDE discovery** — extending parameterized identification to general spatio-temporal PDEs
- **Integration with neural operators** — coupling ADAM-SINDy with latent-space representations for high-dimensional fields

---

## 📚 Citation

If you use ADAM-SINDy in your research, please cite:

```bibtex
@article{viknesh2026adam_sindy,
  title={ADAM-SINDy: An efficient optimization framework for parameterized nonlinear dynamical system identification},
  author={Viknesh, Siva and Tatari, Younes and Christenson, Chase and Arzani, Amirhossein},
  journal={Physical Review Research},
  volume={8},
  pages={013040},
  year={2026},
  doi={10.1103/dwkk-5g2h}
}
```
