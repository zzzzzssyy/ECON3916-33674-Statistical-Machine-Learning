# 🛠️ Data Wrangling & Engineering Pipeline

## 🎯 Objective

Engineer structural features and impute missing values to prepare a chaotic, real-world HR dataset for rigorous econometric modeling — transforming raw, unusable data into a clean, model-ready analytical asset.

---

## 📦 The Data

**Source:** `messy_hr_economics.csv` — a synthetically corrupted HR economics dataset containing employee records with salary, tenure, department, bonus pay, performance ratings, and high-cardinality geographic identifiers (ZIP codes).

**Stack:** 🐍 Python · 🐼 pandas · 📊 statsmodels · 🔍 missingno · 🔠 category_encoders

---

## ⚙️ Methodology

**1. 📥 Data Ingestion**
Loaded the dataset programmatically from a remote repository using `pandas.read_csv()` to simulate a real-world ETL pipeline entry point.

**2. 🔬 Visual Forensics (Missingness Diagnosis)**
Applied `missingno.matrix()` to render the dataset's missingness structure as a visual heatmap. Identified that missing values in `bonus_pay` and `performance_rating` were structurally aligned — a diagnostic signature of **Missing at Random (MAR)**, where absence in one variable predicts absence in another.

**3. 🩹 Conditional Median Imputation**
Replaced missing values using group-conditional median imputation via `pandas.groupby().transform()`. This method preserves distributional integrity within subgroups (e.g., department), avoiding the bias introduced by global mean/median substitution.

**4. 🪤 Dummy Variable Engineering & Multicollinearity Mitigation**
Encoded the `department` categorical variable using `pd.get_dummies()`. Applied the **k-1 methodology** (`drop_first=True`) to establish a reference category and prevent the **Dummy Variable Trap** — a form of perfect multicollinearity that causes OLS estimation to fail due to a singular design matrix.

**5. 🗜️ High-Cardinality Encoding via Target Encoding**
The `office_zip` column contained ~800 unique ZIP codes — too high-cardinality for standard one-hot encoding. Applied `category_encoders.TargetEncoder` to compress this dimension into a single continuous variable representing the conditional mean of `base_salary` within each ZIP code, making the feature viable for regression without dimensionality explosion.

**6. 📈 OLS Regression Validation**
Fitted an Ordinary Least Squares model using `statsmodels.OLS` to validate the engineered features. Confirmed model stability (Condition Number reduced from `6.44e+15` to `17.2`) after applying the k-1 encoding fix, with an R² of **0.744** and all predictors statistically significant at p < 0.001.

---

## 🔑 Key Findings

- 🕵️ **Structural missingness detected:** `bonus_pay` and `performance_rating` exhibited aligned gaps consistent with a MAR mechanism, not random noise — a pattern invisible to summary statistics alone.
- ✅ **Multicollinearity neutralized:** Full dummy encoding produced a near-singular matrix (Condition Number `6.44e+15`); dropping the reference category reduced it to `17.2`, restoring numerical stability.
- 📉 **Dimensionality compressed:** Target encoding reduced ~800 ZIP code dummies to a single informative continuous feature without information loss.
- 🏆 **Model performance:** Final OLS model achieved R² = 0.744, with `tenure_years` and department membership as the dominant salary predictors.

---

## 💡 Skills Demonstrated

`Exploratory Data Analysis` · `Missing Data Theory (MCAR / MAR / MNAR)` · `Feature Engineering` · `Categorical Encoding` · `Multicollinearity Detection` · `OLS Regression` · `Python (pandas, statsmodels, missingno, category_encoders)`
