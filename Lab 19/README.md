# 🌲 Random Forest vs OLS — California Housing Price Prediction

## 🎯 Objective
Compare the predictive performance of Decision Trees, Ridge Regression, and Random Forests on California Housing data, demonstrating how ensemble methods overcome the bias-variance tradeoff limitations of single models.

## 🔧 Methodology
- 📡 **Data sourcing:** California Housing dataset — 20,640 observations with 8 features including median income, house age, average rooms, and geographic coordinates, predicting median house value
- 🔬 **Model comparison:** Trained three models side-by-side — an unrestricted Decision Tree (high variance baseline), Ridge Regression (Ch 16 linear callback), and a Random Forest (100 trees) — evaluating each on Train RMSE, Test RMSE, Train R², and Test R²
- 📊 **Feature importance:** Computed and compared MDI (Mean Decrease in Impurity) and permutation importance to identify the most predictive features, highlighting the distinction between predictive correlation and causal inference
- ⚙️ **Hyperparameter tuning:** Applied GridSearchCV with 5-fold cross-validation across n_estimators (50/100/200), max_depth (10/20/None), and max_features (sqrt/0.5/None) to find the optimal Random Forest configuration
- 🏷️ **Classification extension:** Converted the regression target into a binary label (above/below median price) and compared Random Forest Classifier against Logistic Regression using ROC-AUC and PR-AUC
- 📈 **Partial dependence plots:** Visualized the marginal effect of MedInc and AveOccup on predicted housing prices, revealing the non-linear relationships that OLS cannot capture

## 💡 Key Findings
- 🚨 The unrestricted Decision Tree achieved a perfect Train R² of **1.00** but collapsed to **0.62** on the test set — a textbook case of high-variance overfitting that motivates ensemble methods
- ✅ Random Forest substantially outperformed Ridge Regression on Test R² (**0.81 vs 0.58**), confirming that the relationship between features and housing prices is non-linear and cannot be adequately modeled with linear assumptions
- ⚙️ GridSearchCV identified optimal parameters of **200 trees, full depth, and sqrt features**, improving Test R² from 0.8051 to **0.8138** and reducing Test RMSE from 0.5053 to **0.4939**
- 🏆 The Random Forest Classifier achieved an AUC of **0.9611** vs Logistic Regression's **0.9060** — a practically significant gap in a real estate classification context where misclassification carries financial consequences
- 🔗 MedInc was the top feature by both MDI and permutation importance, but this reflects predictive correlation rather than causation — a DAG analysis would be required to identify any causal pathway from income to housing prices

## 🛠️ Tech Stack
`Python` · `pandas` · `numpy` · `scikit-learn` · `matplotlib` · `seaborn`
