# 📉 NY Fed Yield Curve Recession Model Replication

## 🎯 Objective
Replicate the Federal Reserve Bank of New York's yield curve recession model by applying logistic regression to FRED macroeconomic data, generating a forward-looking probability estimate of NBER-defined recessions 12 months ahead.

## 🔧 Methodology
- 📡 **Data sourcing:** Retrieved two FRED series via API — T10Y3M (10-Year minus 3-Month Treasury yield spread, daily, resampled to month-end) and USREC (NBER recession indicator, monthly) — covering January 1970 to present
- ⚙️ **Feature engineering:** Applied a 12-month lag to the yield spread to align the predictor with the forward recession window, consistent with the NY Fed's original specification
- 🔬 **Model comparison:** Estimated a Linear Probability Model (OLS) alongside a logistic regression (sklearn LogisticRegression) to empirically demonstrate the LPM's theoretical failure — producing fitted probabilities outside [0, 1] on real macroeconomic data
- 📊 **Inference:** Re-estimated the logistic model using statsmodels Logit to extract the yield spread odds ratio with 95% confidence intervals, enabling formal hypothesis testing
- ➕ **Extended model:** Added a second FRED predictor (UNRATE, unemployment rate, lagged 12 months) to a two-predictor logistic regression and compared odds ratios across the one- and two-predictor specifications
- 📈 **Visualization:** Constructed the full recession probability time series from 1970 to present, overlaid with NBER recession shading, replicating the NY Fed's signature chart

## 💡 Key Findings
- 🔑 The yield spread odds ratio is approximately **0.45**, indicating that a wider (more positive) spread is associated with substantially lower recession probability — consistent with the NY Fed model's interpretation
- ❌ The Linear Probability Model produced fitted probabilities below 0% and above 100% on actual data, confirming its unsuitability for binary outcome forecasting and motivating the logistic specification
- ⚠️ During the 2022–2024 yield curve inversion — the deepest in modern history — the model predicted recession probability peaking above **40%**, yet no NBER recession materialized; this illustrates that probabilistic forecasts reflect historical base rates, not deterministic predictions
- 🔗 Adding the unemployment rate as a second predictor increased the yield spread's odds ratio slightly (0.454 → 0.565), suggesting partial multicollinearity between the two recession signals; neither predictor reached conventional statistical significance in the joint model, indicating the yield spread alone captures much of the available recession information

## 🛠️ Tech Stack
`Python` · `pandas` · `numpy` · `scikit-learn` · `statsmodels` · `matplotlib` · `fredapi`
