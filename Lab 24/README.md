Causal ML — Double Machine Learning for 401(k) Policy Evaluation
Objective

Estimate the causal effect of 401(k) eligibility on household net financial assets using modern Double Machine Learning methods, and evaluate heterogeneity across income groups.

Methodology
Simulated a data-generating process (DGP) to demonstrate regularization bias, showing that naïve LASSO underestimates treatment effects by shrinking coefficients toward zero
Implemented a Double Machine Learning (DML) Partially Linear Regression (PLR) framework
Used Random Forests as flexible nuisance learners for outcome and treatment models
Applied 5-fold cross-fitting to reduce overfitting and ensure valid inference
Estimated the Average Treatment Effect (ATE) of 401(k) eligibility on net financial assets
Conducted Conditional Average Treatment Effect (CATE) analysis across income quartiles
Visualized subgroup effects with confidence intervals to assess statistical significance and heterogeneity
Key Findings
The DML estimate suggests that 401(k) eligibility has a positive effect on net financial assets, though the magnitude is estimated with substantial uncertainty
Naïve LASSO produced a downward-biased treatment estimate, confirming the presence of regularization bias in causal settings
CATE estimates vary across income quartiles in magnitude, but none are statistically significant, as all confidence intervals include zero
These results suggest no strong empirical evidence of heterogeneous treatment effects by income, despite theoretical expectations of larger effects for higher-income households
