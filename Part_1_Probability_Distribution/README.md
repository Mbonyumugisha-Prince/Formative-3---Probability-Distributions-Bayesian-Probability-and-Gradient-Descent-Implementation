# Part 1 — Bivariate Normal Distribution (From Scratch)

## Overview

This section implements the **Bivariate Normal (BVN) Probability Density Function** entirely from scratch — no statistical libraries are used. We compute sample statistics manually and derive the PDF formula in pure Python, then visualise the results with Matplotlib.

## Dataset

**Brain MRI Radiomics-Style Numerical Dataset**

- **Source:** <https://www.kaggle.com/datasets/aadigupta1601/brain-mri-radiomics-style-numerical-dataset>
- **File:** `brain_mri_rich_features.csv` (7 023 records, 28 columns)
- **Selected features:** `mean` (average pixel intensity) and `energy` (texture descriptor)

## Methodology

1. **Load** the dataset and extract the two chosen continuous features.
2. **Compute** the five BVN parameters from scratch:
   - Means: μ₁, μ₂
   - Standard deviations: σ₁, σ₂
   - Pearson correlation coefficient: ρ
3. **Implement** the BVN PDF formula:

$$
f(x, y) = \frac{1}{2\pi\,\sigma_1\,\sigma_2\,\sqrt{1-\rho^2}}
\;\exp\!\left(
  -\frac{1}{2(1-\rho^2)}
  \left[
    \left(\frac{x-\mu_1}{\sigma_1}\right)^{2}
    - 2\rho\,\frac{(x-\mu_1)(y-\mu_2)}{\sigma_1\,\sigma_2}
    + \left(\frac{y-\mu_2}{\sigma_2}\right)^{2}
  \right]
\right)
$$

4. **Evaluate** the PDF on every data point and on a visualisation grid.
5. **Visualise** with:
   - A **contour plot** showing the characteristic elliptical density contours.
   - A **3D surface plot** showing the bell-shaped PDF surface.

## Files

| File | Description |
|------|-------------|
| `bivariate_normal_distribution.ipynb` | Jupyter notebook with full implementation and plots |
| `brain_mri_rich_features.csv` | Source dataset |
| `README.md` | This documentation |

## How to Run

```bash
cd Part_1_Probability_Distribution
jupyter notebook bivariate_normal_distribution.ipynb
```

## Key Observations

- The elliptical contours confirm the bivariate normal shape; their tilt reflects the correlation **ρ** between the two features.
- The 3D surface peaks at the joint mean (μ₁, μ₂) and decays according to the covariance structure **Σ**.
- Parameters μ, Σ, and ρ directly govern the distribution's location, spread, and orientation.