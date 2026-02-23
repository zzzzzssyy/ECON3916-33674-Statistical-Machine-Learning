The Epistemology of Falsification: Hypothesis Testing on the Lalonde Dataset
Project Title: Hypothesis Testing & Causal Evidence Architecture

Objective
This project operationalizes a fundamental shift in analytical philosophy — moving from Estimation (reporting a number) to Falsification (stress-testing a claim). Using the Lalonde (1986) dataset, I adjudicate between competing narratives of causality to determine whether a job training intervention produced a measurable effect on real earnings.
The guiding question is not "What is the treatment effect?" but rather "Can the Null Hypothesis of zero effect be credibly rejected, and under what conditions does that rejection hold?"

Methodology
Parametric Testing — Signal-to-Noise Ratio via Welch's T-Test

Calculated the Average Treatment Effect (ATE) of job training on 1978 real earnings by comparing the treated and control groups.
Applied Welch's T-Test (unequal variance formulation) as the primary signal-to-noise estimator, producing a t-statistic and p-value under the assumption of approximately normal sampling distributions.
Controlled for Type I error rate at the conventional α = 0.05 threshold, with awareness that threshold selection is a business parameter, not a universal scientific law.

Non-Parametric Validation — Permutation Test (10,000 Resamples)

Conducted a Permutation Test with 10,000 resamples to construct an empirical null distribution free from distributional assumptions.
This approach is robust to the non-normality observed in earnings distributions (right-skewed, zero-inflated), serving as a validation layer against the parametric result.
The convergence of parametric and non-parametric results under consistent conclusions strengthens the inferential architecture.


Key Findings

Detected a statistically significant lift in real earnings of approximately ~$1,795 for participants in the job training program.
Null Hypothesis rejected via Proof by Statistical Contradiction: the probability of observing an effect this large under the null is below the accepted decision threshold.
Results are consistent across both the parametric (Welch's T-Test) and non-parametric (Permutation Test) frameworks, ruling out distributional artifacts as a confounding explanation.


Technical Approach

Libraries: scipy.stats for parametric testing; numpy for permutation resampling logic.
Type I Error Control: Significance threshold explicitly set and justified, not assumed — acknowledging that α is a decision boundary calibrated to the cost of false positives in the given business context.
Dual-Method Validation: Parametric and non-parametric methods deployed in parallel to cross-validate conclusions and guard against model misspecification.
Reproducibility: Random seed fixed for permutation test to ensure deterministic replication of the empirical null distribution.


Business Insight: Hypothesis Testing as the Safety Valve of the Algorithmic Economy
In the modern data economy, the ability to calculate a statistic is a commodity. The scarce and valuable skill is Causal Evidence Architecture — the capacity to design tests that distinguish genuine signal from noise, and to recognize when an observed effect is an artifact of data collection rather than a feature of reality.
Rigorous hypothesis testing functions as the Safety Valve of algorithmic decision-making. Without it, organizations fall prey to:

Data Grubbing: Iterating over metrics until a significant result appears by chance, inflating false discovery rates.
Spurious Correlations: Optimizing on patterns that do not generalize, leading to flawed product decisions at scale.
Survivorship Bias: Drawing conclusions from visible outcomes while ignoring the structure of the data-generating process.

Companies like Netflix and Uber do not ask "Is the p-value below 0.05?" They ask "Is the experimental design valid?" and "Are we controlling for the right confounders?" This project reflects that professional standard — treating hypothesis testing not as a checklist item, but as a framework for principled belief revision under uncertainty.
