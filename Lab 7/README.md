# 🤖 Lab 7: The Engine of Inference

This lab examines how modeling assumptions shape risk estimation.
Specifically, we analyze how ignoring correlation between economic variables structurally distorts simulation outputs.

The focus is not coding mechanics — but inference architecture.

---

## 🧩 1. Independence Assumption & Risk Inflation

**Problem:**
The “naive” simulation assumed Revenue and Burn were independent.

In reality:
[
\rho(\text{Revenue}, \text{Burn}) \approx 0.7
]

When revenue drops, management cuts burn.
The independent model ignores this adaptive behavior.

**Structural Risk:**
Independence artificially increases downside dispersion and overstates ruin probability.

---

## ⚙️ 2. Refactoring the Simulation

**Method:**
Replaced independent normal draws with correlated sampling:

* Used `numpy.random.multivariate_normal`
* Maintained original means and standard deviations
* Introduced covariance structure:

[
\Sigma =
\begin{pmatrix}
\sigma_R^2 & \rho\sigma_R\sigma_B \
\rho\sigma_R\sigma_B & \sigma_B^2
\end{pmatrix}
]

This embeds realistic economic co-movement.

---

## 📉 3. Comparative Outcome

**Finding:**

* Independent Model → Ruin Probability ≈ 15%
* Correlated Model → Ruin Probability ≈ 5%

The correlation acts as a **natural hedge**:

* When revenue is weak, burn adjusts downward
* Downside tails compress

Volatility of net cash flow decreases.

---

## 🧠 4. Inference Insight

This lab demonstrates a deeper principle:

> Incorrect structural assumptions distort probabilistic inference more than parameter misspecification.

Independence is not neutral.
It encodes a belief about how the world behaves.

Simulation outputs are only as valid as the dependency structure they assume.

---

## 🔬 Key Takeaway

* Independence ≠ realism
* Correlation embeds adaptive economic behavior
* Risk modeling requires structural coherence

Monte Carlo is not about randomness —
it is about modeling the data-generating process correctly.
