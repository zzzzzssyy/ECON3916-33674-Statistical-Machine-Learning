# The Polynomial Trap: Bias-Variance Tradeoff
### Lab 15 | Data Science Portfolio

## Overview
An end-to-end exploration of the bias-variance tradeoff using polynomial
regression on synthetic sine-wave data and the Ames Housing dataset.
Demonstrates how model complexity drives the gap between training and
test performance — and how cross-validation closes it.

## Key Findings
- Polynomial degrees 3–5 minimized test RMSE on synthetic data
- CV-selected degree matched the true test-optimal degree
- A 5-feature housing model outperformed a 37-feature kitchen-sink
  model in CV RMSE, despite lower training R²
- Bias² + Variance + σ² ≈ MSE, verified via 100 bootstrap samples

## Contents
| File | Description |
|------|-------------|
| `Lab15_BiasVariance.ipynb` | Main notebook with all analysis |
| `bias_variance_dashboard.py` | Interactive Streamlit dashboard |
| `README.md` | This file |

## Tools & Libraries
`Python` `numpy` `scikit-learn` `matplotlib` `streamlit`

## Running the Dashboard
```bash
pip install streamlit scikit-learn matplotlib numpy
streamlit run bias_variance_dashboard.py
```

## Concepts Demonstrated
- Polynomial regression & PolynomialFeatures
- Complexity curves (train vs. test RMSE)
- K-fold cross-validation for model selection
- Bootstrap bias-variance decomposition
- Overfitting, underfitting, irreducible error
