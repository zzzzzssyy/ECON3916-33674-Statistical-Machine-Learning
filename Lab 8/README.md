The Epistemology of Falsification
Hypothesis Testing on the Lalonde Dataset
The guiding question is not "What is the treatment effect?" — it is "Can the Null Hypothesis of zero effect be credibly rejected, and under what conditions does that rejection hold?" This project operationalizes a shift from Estimation to Falsification.

Prompt 1 — README.md · Lab 8 Folder
🎯
Objective
Project Title: Hypothesis Testing & Causal Evidence Architecture
Using the Lalonde (1986) dataset, I adjudicate between competing narratives of causality to determine whether a job training intervention produced a measurable effect on real earnings. The analytical philosophy pivots from Estimation (reporting a number) to Falsification (stress-testing a claim against a principled null model).
⚙️
Methodology
Parametric — Welch's T-Test
Estimated Average Treatment Effect (ATE) on 1978 real earnings
Welch's formulation handles unequal variances between groups
Produced t-statistic and p-value under normal sampling assumption
Type I error controlled at explicit α threshold
Non-Parametric — Permutation Test
10,000 resamples to build empirical null distribution
Robust to right-skewed, zero-inflated earnings data
Validates parametric result without distributional assumptions
Convergence of both methods strengthens inference
📊
Key Findings
+$1,795
Statistically significant lift in real earnings for job training participants. Null Hypothesis rejected via Proof by Statistical Contradiction — results consistent across both parametric and non-parametric frameworks, ruling out distributional artifacts as a confounding explanation.
🛠️
Technical Approach
Dual-method validation deployed in parallel to cross-validate conclusions and guard against model misspecification. Significance threshold explicitly set and justified — acknowledging that α is a decision boundary calibrated to the cost of false positives, not a universal scientific default.

scipy.stats — T-Test
numpy — Permutation Resampling
Random Seed Fixed — Reproducible
Type I Error Control
Welch's Formulation
💡
Business Insight: Hypothesis Testing as the Safety Valve
In the modern data economy, calculating a statistic is a commodity. The scarce skill is Causal Evidence Architecture — designing tests that distinguish genuine signal from noise. Without rigorous hypothesis testing, organizations fall prey to:

🎲
Data Grubbing
Iterating over metrics until significance appears by chance, inflating false discovery rates.

🔀
Spurious Correlations
Optimizing on patterns that don't generalize, leading to flawed product decisions at scale.

🪄
Survivorship Bias
Drawing conclusions from visible outcomes while ignoring the data-generating process.

Companies like Netflix and Uber don't ask "Is the p-value below 0.05?" — they ask "Is the experimental design valid?" and "Are we controlling for the right confounders?" This project treats hypothesis testing not as a checklist item, but as a framework for principled belief revision under uncertainty.
Prompt 2 — Concept Extension · Portfolio README
🧠
Return-Aware Experimentation — Concept Extension
3–4 sentences · Portfolio-ready
Return-Aware Experimentation is Netflix's framework for calibrating decision thresholds to the asymmetric cost of errors, rather than applying a uniform p < 0.05 standard borrowed from academic convention. Where academic statistics treats α = 0.05 as a near-universal norm, Netflix recognizes that the cost of a false positive (shipping a harmful feature to 200M users) is categorically different from the cost of a false negative (delaying a beneficial one). This means decision thresholds are business parameters — tuned to the revenue, risk, and reversibility of each specific decision — not immutable scientific laws. I apply this principle by treating my significance thresholds as explicit choices I can defend, not defaults I inherit.
