# IMF Early Warning System (EWS)

## Overview
This project builds a next-generation Early Warning System for the IMF's Global Financial Stability Division. The goal is to predict whether a country will experience a growth crisis (sustained negative GDP per capita growth) within a given period, using World Development Indicators (WDI) from the World Bank API.

## Structure
The notebook is organized into four phases:

**Shared Data Pipeline**
Downloads 30+ WDI indicators for ~150 countries (2013–2019 averages) via the World Bank API, constructs the binary crisis outcome, and splits data into train/test sets.

**Phase 1: The Complexity Trap — OLS Failure and Regularization Rescue**
Demonstrates OLS overfitting using bias-variance analysis, applies Ridge and Lasso regularization with cross-validation, and traces the Lasso coefficient path to identify which indicators enter the model first.

**Phase 2: The Crisis Classifier — From Forecasting to Classification**
Exposes the failure of the Linear Probability Model, builds a logistic regression crisis classifier, computes odds ratios, and visualizes LPM vs. logistic regression side by side.

**Phase 3: Operational Deployment — Metrics That Matter**
Evaluates the classifier using the full toolkit of classification metrics including the accuracy paradox, confusion matrix, ROC and Precision-Recall curves, and threshold analysis under IMF operational constraints.

**Phase 4: AI Context Engineering — The P.R.I.M.E. Framework**
Uses the P.R.I.M.E. framework to direct an LLM to perform bootstrap Lasso stability analysis and cost-sensitive threshold optimization.

## Requirements
## How to Run
Open the notebook in Google Colab or Jupyter, then run Kernel > Restart & Run All. No CSV files are needed as all data is downloaded live from the World Bank API.

## Data
- Source: World Bank API via wbgapi
- Time period: 2013–2019 averages
- Coverage: ~150 countries
- Predictors: 30+ WDI indicators across trade, macroeconomics, education, infrastructure, health, finance, natural resources, agriculture, and governance
- Outcome: Binary crisis indicator (crisis = 1 if average GDP per capita growth < 0)

## Key Results
- OLS severely overfits due to high p/n ratio, producing near-perfect training R² but poor test R²
- Lasso outperforms OLS and Ridge by selecting a sparse set of the most informative indicators
- Logistic regression correctly constrains predicted probabilities to [0, 1] unlike the Linear Probability Model
- The cost-minimizing threshold is much lower than the F1-optimal threshold due to the extreme asymmetry between missed crisis cost ($50B) and false alarm cost ($2M)
