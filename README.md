# 📈 dupire-local-vol-surface

## Local Volatility Model – Dupire Framework

---

## Overview

This project aims to construct a **local volatility surface** from market European option prices using the Dupire framework.

We seek to recover a deterministic volatility function  

\[
\sigma_{\text{loc}}(S,t)
\]

such that the risk-neutral diffusion

\[
dS_t = r S_t\,dt + \sigma_{\text{loc}}(S_t,t)\,S_t\,dW_t
\]

reproduces observed vanilla option prices across strikes and maturities.

The project focuses on the mathematical derivation, numerical stability considerations, and practical calibration challenges involved in implementing the Dupire inversion.

---

## Motivation

The Black–Scholes model assumes constant volatility, which is inconsistent with observed implied volatility smiles and skews.

Local volatility models generalise this by allowing volatility to depend on both spot and time. The Dupire formula provides a way to infer this surface directly from market data.

This project explores:

- The relationship between option prices and risk-neutral densities  
- The forward (Fokker–Planck) equation associated with diffusion models  
- The inversion of option prices to obtain local volatility  
- Numerical instability arising from second derivatives  

---

## Mathematical Framework

Starting from the call price representation

\[
C(K,T) = e^{-r(T-t)} \int_K^{\infty} (S' - K)\, p(S,t;S',T)\, dS',
\]

and using the forward Kolmogorov equation for the density \(p\), one obtains the Dupire equation

\[
\frac{\partial C}{\partial T}
=
\frac{1}{2} \sigma_{\text{loc}}^2(K,T) K^2 \frac{\partial^2 C}{\partial K^2}
-
rK \frac{\partial C}{\partial K}.
\]

Solving for local variance yields

\[
\sigma_{\text{loc}}^2(K,T)
=
\frac{\partial_T C + rK\,\partial_K C}
{\tfrac12 K^2\,\partial_{KK} C}.
\]

This inversion forms the core of the model.

---

## Key Numerical Challenges

The Dupire approach presents several practical issues:

- Requires a continuum of strikes and maturities  
- Numerical differentiation is ill-conditioned  
- Second strike derivatives may become small in the wings  
- Market data contains noise and bid–ask spreads  

Stabilisation and regularisation techniques are therefore central to any robust implementation.

---

## Planned Components

The project is structured around the following stages:

1. Construction of a smooth implied volatility surface  
2. Conversion of implied volatility to price space  
3. Numerical estimation of partial derivatives  
4. Computation of the local volatility surface  
5. Validation via pricing consistency checks  

Implementation details and numerical schemes will be documented as development progresses.

---

## Intended Extensions

Potential extensions include:

- Comparison with stochastic volatility models  
- Discussion of local–stochastic volatility  
- Analysis of smile dynamics  
- PDE vs Monte Carlo validation  

---

## Technical Stack

Implementation will be done in Python, with emphasis on:

- Numerical stability  
- Vectorised computation  
- Clear modular structure  
- Reproducibility  

Further technical details will be added as development progresses.

---

## References

- Dupire (1994), *Pricing with a Smile*  
- Gatheral, *The Volatility Surface*  
- Advanced Volatility Modelling lecture notes  

---

## Status

Project in progress.  
Mathematical framework established; implementation phase forthcoming.
