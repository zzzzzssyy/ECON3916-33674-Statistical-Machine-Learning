📊 Assignment 2: The Algorithmic Audit

This audit examines how seemingly “strong” metrics can systematically mislead decision-makers when robustness, base rates, or missing data are ignored.

The analysis is structured around three statistical failure mechanisms.

🧱 1. Latency Skew & Fragile Metrics

Problem: Aggregate latency metrics were distorted by a small number of extreme delays.

Method:
Compared Standard Deviation (SD) with Median Absolute Deviation (MAD) under simulated heavy-tail conditions.

Finding:

SD increased dramatically after introducing a small cluster of extreme outliers

MAD remained stable and better reflected typical system behavior

Insight:
Metrics based on squared deviations are fragile under skew.
Robust statistics are essential in heavy-tailed environments.

🎯 2. False Positives & Base Rate Neglect

Problem: A classifier advertised “98% accuracy” without accounting for prevalence.

Method:
Conducted a Bayesian posterior audit:

𝑃
(
True Event
∣
Flagged
)
P(True Event∣Flagged)

across varying base rates.

Finding:

In low-incidence environments, the majority of flagged cases were false positives

High sensitivity and specificity did not translate into reliable decision quality

Insight:
Accuracy without base rate context is statistically misleading.
Ignoring prevalence converts strong-looking metrics into institutional risk.

🧬 3. Survivorship Bias & Missing Failures

Problem: Performance was reported using only surviving entities.

Method:
Simulated full population outcomes using a heavy-tailed (Pareto) distribution and compared:

Full population mean

Survivor-only mean

Finding:

Survivor-only averages were orders of magnitude higher

Excluding failures created a false narrative of consistent success

Insight:
Deleting failures is equivalent to altering the data-generating process.

✅ Key Takeaway

Statistical distortions rarely arise from incorrect arithmetic.
They emerge from flawed structural assumptions.

Latency skew hides temporal incompleteness

False positives hide prevalence structure

Survivorship bias hides population attrition

Robust metrics, Bayesian reasoning, and full denominator visibility are not optional — they are foundational to analytical integrity.
