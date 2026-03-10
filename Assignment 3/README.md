📊 Assignment 3: Causal Inference & Non-Parametric Statistics
This assignment examines how naive statistical comparisons can systematically mislead decision-makers when distributional assumptions are violated or selection bias is ignored.
The analysis is structured around three statistical inference challenges.

🥾 1. Non-Parametric Uncertainty via Bootstrap
Problem: Driver tip data is heavily zero-inflated and right-skewed, rendering the Central Limit Theorem unreliable for small-sample median estimation.
Method: Manually implemented a Bootstrap engine using NumPy — 10,000 with-replacement resamples of 250 driver tips, computing the sample median each iteration. Extracted a 95% Confidence Interval via np.percentile.
Finding:

The 95% CI was asymmetric around the sample median
The upper bound extended further than the lower bound, reflecting the right skew of the data

Insight: Standard parametric confidence intervals assume symmetry and fail in zero-inflated distributions. Bootstrap captures the true shape of sampling uncertainty without distributional assumptions.

🔀 2. Falsification via Permutation Testing
Problem: A new "Batch Routing" algorithm showed improved delivery times on average, but extreme upper-bound outliers from software crash loops invalidated the homoscedasticity assumption of a standard T-test.
Method: Manually constructed a Permutation Test — concatenated 1,000 deliveries (500 Control, 500 Treatment), then ran 5,000 random shuffles using np.random.permutation, computing the difference in means each iteration. Calculated the exact empirical p-value.
Finding:

The observed difference in means was compared against the null distribution of 5,000 permuted differences
The empirical p-value reflects the exact probability under the null with no parametric assumptions

Insight: When variance is unequal across groups, permutation tests provide an exact, assumption-free alternative to the T-test that is robust to outliers and distributional skew.

⚖️ 3. Causal Control & Mitigation of Selection Bias
Problem: Users who subscribe to the "SwiftPass" loyalty program appeared to spend significantly more — but high-volume "power users" self-select into the program, creating severe selection bias in the naive comparison.
Method: Applied Propensity Score Matching (PSM) — estimated propensity scores via LogisticRegression on pre-treatment covariates (pre_spend, account_age, support_tickets), then matched each subscriber to the nearest non-subscriber using 1-NN on propensity score. Computed the ATT on the matched sample.
Finding:

Naive SDO (Simple Difference in Means): 17.57
Causal ATT after PSM: 9.91
A Love Plot confirmed successful covariate balance after matching

Insight: The gap between SDO and ATT confirms that over half of the raw spending difference was attributable to selection bias, not the loyalty program itself. Ignoring pre-treatment differences converts a causal question into a misleading correlation.
