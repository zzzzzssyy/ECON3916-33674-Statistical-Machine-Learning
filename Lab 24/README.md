## Causal ML — Double Machine Learning for 401(k) Policy Evaluation

### Objective
Estimate the causal effect of 401(k) eligibility on household net financial assets using Double Machine Learning, and assess whether the effect varies across income groups.

### Methodology
- Demonstrated regularization bias using a simulated DGP (TRUE_ATE = 5.0), showing that naïve LASSO shrinks the treatment effect toward zero
- Implemented a Double Machine Learning (DML) Partially Linear Regression (PLR) model
- Used Random Forests as nuisance learners for outcome and treatment estimation
- Applied 5-fold cross-fitting to ensure valid causal inference
- Estimated the Average Treatment Effect (ATE) of 401(k) eligibility on net financial assets
- Conducted Conditional ATE (CATE) analysis across income quartiles
- Visualized subgroup estimates with confidence intervals

### Key Findings
- DML produces a more reliable estimate of the treatment effect compared to naïve LASSO, which is biased due to regularization
- 401(k) eligibility shows a positive but imprecisely estimated effect on net financial assets
- CATE estimates differ across income quartiles in magnitude, but none are statistically significant
- Overall, there is no strong evidence that the treatment effect varies systematically by income level
