# Kernel Gradient Discrepancy as a Diagnostic for Wasserstein Gradient Flow



A research notebook exploring Kernel Gradient Discrepancy (KGD) as a
stopping criterion and diagnostic for Wasserstein Gradient Flow (WGF)
implementations in `pymc-prop`.

This repository provides a translation between the mathematical formulation
of KGD in the literature and its practical use within the PrO framework,
with the goal of developing an interpretable convergence diagnostic for users.

---

## Motivation

Predictively Oriented (PrO) posteriors redefine parameter uncertainty as a direct consequence of predictive performance rather than relying on standard, model-dependent Bayesian assumptions. In practice, computing these objectives requires moving particle swarms across probability space via Wasserstein Gradient Flow (WGF).

However, because entropy-regularized variational objectives lack an explicit unnormalised density target outside standard Bayesian settings, tracking optimization and knowing when the particle swarm has reached its predictively optimal configuration is a major computational challenge.

This notebook investigates Kernel Gradient Discrepancy (KGD) as a principled diagnostic and stopping criterion for the process of calculating PrO models implemented in pymc-prop. By monitoring the magnitude of the kernelized variational gradient along the WGF trajectory, KGD provides a quantitative criterion to determine convergence.

The aims of this project are:

- understand the mathematical notation and derivation of KGD from the
  relevant literature;
- translate the paper's notation into the notation used by `pymc-prop`;
- implement and validate the required kernel-based diagnostics;
- expose KGD values through user-facing outputs such as ArviZ
  `InferenceData`;
- investigate how KGD behaves under different WGF configurations.

---

## Objectives

The notebook will demonstrate:

### 1. Mathematical translation

A detailed explanation connecting:

- the paper's formulation of Wasserstein Gradient Flow;
- the KGD convergence diagnostic;
- the corresponding objects and notation used in `pymc-prop`.

---

### 2. User-facing diagnostics

The notebook will demonstrate how KGD could be exposed to users through:

- KGD trace plots across WGF time steps;
- storage of KGD diagnostics in returned ArviZ `InferenceData`;
- interpretation of KGD trajectories;
- guidance on what users should look for when assessing convergence.

---

### 3. Experimental investigation

Small computational experiments will explore the effect of changing WGF parameters, including:

- particle count;
- WGF step size;
- other relevant simulation parameters.

The aim is to understand how these choices influence:

- convergence behaviour;
- KGD trajectories;
- stopping decisions.

---

## Repository Structure
