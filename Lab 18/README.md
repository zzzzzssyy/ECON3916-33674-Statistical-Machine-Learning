# 🕵️ Fraud Detection Model Evaluation — Metrics that Matter

## 🎯 Objective
Evaluate a logistic regression fraud detector beyond simple accuracy — using confusion matrices, Precision, Recall, F1-Score, ROC curves, Precision-Recall curves, and threshold analysis on a severely imbalanced real-world dataset (0.172% positive class).

## 🔧 Methodology
- 📡 **Data sourcing:** Kaggle Credit Card Fraud Detection dataset — 284,807 real-world European credit card transactions with PCA-anonymized features V1–V28, transaction Amount, and a binary fraud label
- ⚠️ **Baseline critique:** Established the accuracy paradox — a naive model predicting "no fraud" on every transaction achieves **99.83% accuracy** while detecting zero frauds, exposing accuracy as a meaningless metric on imbalanced data
- 🔬 **Model training:** Fitted a logistic regression classifier (sklearn LogisticRegression) with scaled features, generating predicted probabilities for the positive (fraud) class
- 📊 **Threshold analysis:** Evaluated Precision, Recall, and F1-Score across the full threshold range [0.01, 0.99], demonstrating that the F1-optimal threshold differs materially from the conventional 0.5 default
- 📈 **Curve analysis:** Plotted ROC and Precision-Recall curves, computing ROC-AUC and PR-AUC to compare model performance — with emphasis on PR-AUC as the more informative metric for severely imbalanced classification
- 💼 **Business constraint:** Applied a capacity constraint (maximum 500 daily fraud investigations) to identify a business-relevant operating point on the Precision-Recall curve, translating model output into an actionable decision rule

## 💡 Key Findings
- 🚫 The naive all-negative baseline achieves **99.83% accuracy** with zero fraud recall — confirming that accuracy is an unreliable metric for imbalanced fraud detection and motivating the use of Precision, Recall, and F1
- ✅ Logistic regression achieved strong **ROC-AUC** and meaningful **PR-AUC** on the fraud class, demonstrating genuine discriminative power despite the severe class imbalance
- 🎚️ The **F1-optimal threshold** differs significantly from the default 0.5 — defaulting to 0.5 leaves substantial detection performance on the table in fraud contexts
- 🏦 Under a **500-investigation-per-day capacity constraint**, the model's operating point was selected to maximise Recall subject to a Precision floor — making the business tradeoff between missed fraud and false alarms explicit and quantifiable

## 🛠️ Tech Stack
`Python` · `pandas` · `numpy` · `scikit-learn` · `matplotlib` · `seaborn`
