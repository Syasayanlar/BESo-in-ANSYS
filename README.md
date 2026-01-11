# BESO in ANSYS

Bi-directional Evolutionary Structural Optimization (BESO) implementation in ANSYS APDL.

## Files

- **beso_2020.in** - Standard BESO implementation with stress and displacement constraints
- **beso_pnorm.in** - Advanced BESO with p-norm aggregation for stress and displacement constraints, featuring:
  - Dual p-norm aggregation (stress: p=8, displacement: p=6)
  - Fully analytical sensitivities (no numerical differentiation)
  - Augmented Lagrangian method for constraint handling
  - ~2N performance improvement over numerical methods
  - Framework for Low Cycle Fatigue (LCF) constraints (commented out)

## P-Norm Aggregation Method

The p-norm method provides smooth approximation to maximum constraints:

- **Stress**: σ_pnorm = σ_ref × (Σ(σ_i/σ_ref)^p)^(1/p) where p=8
- **Displacement**: d_pnorm = d_ref × (Σ(d_i/d_ref)^p)^(1/p) where p=6

### Advantages
- Analytical sensitivities without numerical differentiation
- Single FEA solve per iteration (vs. 2N for numerical methods)
- Smooth constraint gradients for better convergence
- Accurate approximation of maximum values

## Usage

Run in ANSYS APDL:
```apdl
/INPUT, beso_pnorm, in
```

## References

Key papers on p-norm aggregation:
- Kennedy, G.J. & Martins, J.R.R.A. (2015). Computational Structural Mechanics
- Le, C. et al. (2010). Structural and Multidisciplinary Optimization
- París, J. et al. (2009). Structural and Multidisciplinary Optimization

## Author

Implementation by Suleyman Yasayanlar
