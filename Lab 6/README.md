# 🏗️ Lab 5: The Architecture of Bias

This lab investigates how bias is not merely a statistical accident, but a structural property of data pipelines, sampling mechanisms, and model design choices.

Rather than focusing on individual errors, the lab analyzes how bias becomes embedded in system architecture.

---

## 🧱 1. Sampling Bias & Dataset Construction

**Problem:**
Training data did not represent the full target population.

**Method:**
Compared subgroup distributions between:

* Observed sample
* Intended population baseline

Examined representation ratios across categories.

**Finding:**

* Certain groups were systematically underrepresented
* Model predictions were disproportionately unstable in sparse subgroups

**Insight:**
Bias often originates before modeling begins.
If the sampling frame is distorted, model fairness cannot be restored downstream.

---

## ⚙️ 2. Feature Engineering & Proxy Variables

**Problem:**
Seemingly neutral features acted as hidden proxies for sensitive attributes.

**Method:**
Analyzed correlation structure between:

* Model features
* Protected characteristics
* Prediction outputs

Tested impact of feature removal on prediction distribution.

**Finding:**

* Several high-importance variables were strongly correlated with protected classes
* Removing proxy features reduced disparity but slightly reduced raw accuracy

**Insight:**
Predictive power and fairness can conflict when signal overlaps with social structure.
Optimization alone does not guarantee ethical neutrality.

---

## 📊 3. Evaluation Metrics & Distributional Blind Spots

**Problem:**
Overall accuracy masked subgroup-level error disparities.

**Method:**
Computed:

* Overall accuracy
* False positive rate (FPR) by subgroup
* False negative rate (FNR) by subgroup

Compared macro vs subgroup performance.

**Finding:**

* Aggregate metrics appeared strong
* Error rates varied substantially across groups

**Insight:**
Global metrics conceal local harms.
Fairness must be evaluated distributionally, not just in aggregate.

---

## 🧠 4. Feedback Loops & Structural Reinforcement

**Problem:**
Model outputs influenced future data collection, reinforcing initial bias.

**Method:**
Simulated iterative prediction → selection → retraining cycle.

**Finding:**

* Early prediction errors amplified across iterations
* Minority groups became increasingly underrepresented

**Insight:**
Bias is dynamic.
Without intervention, machine learning systems can magnify structural inequalities over time.

---

## ✅ Key Takeaway

Bias is not a bug.
It is an architectural property.

* Sampling determines representation
* Features encode structure
* Metrics determine visibility
* Feedback loops amplify imbalance

Mitigating bias requires intervention at the system level — not just algorithm tuning.

