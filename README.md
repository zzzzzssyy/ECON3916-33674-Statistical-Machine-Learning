# ECON3916-33674-Statistical-Machine-Learning
```markdown
# 📊 Economic Data Science Portfolio

Hi! I’m an undergraduate economics student building a digital portfolio for **ECON 3916: Statistical & Machine Learning for Economics**. I’m actively preparing for roles in **[Data Analysis / Economic Consulting / Finance]** and using this repository to demonstrate how I connect **traditional economic reasoning** with **modern data science workflows**.

---

## About this Portfolio

This repository hosts my **coursework, labs, and applied exercises** from ECON 3916. The course emphasizes a **Concept Extension** approach: we start with core statistical foundations (e.g., OLS regression and inference) and extend them into scalable machine learning methods (e.g., **regularization with Lasso**) to handle higher-dimensional data and improve out-of-sample performance.

My goal in this portfolio is to show that I can work across two complementary perspectives:

- **Causal inference:** asking “what is the effect?” using econometric thinking, identification logic, and careful interpretation.
- **Predictive analytics:** asking “what will happen next?” using machine learning models, validation, and performance-focused evaluation.

In other words, I’m learning to **bridge explanation and prediction**—bringing economic intuition to model design while using data-driven methods to strengthen empirical analysis.

---

## Tech Stack

- 🐍 **Python**
- 🧮 **Pandas**
- 🤖 **Scikit-learn**
- ☁️ **Google Colab**
- 📈 **Statsmodels**

---

## What You’ll Find Here

- **Labs & assignments** applying statistical learning methods to economic datasets  
- **Modeling workflows** (data cleaning, feature engineering, training, evaluation)  
- **Interpretable results** with an emphasis on economic meaning, not just accuracy  

---
## Global Purchasing Power Parity Analysis (Big Mac Index)

### Objective  
Evaluate the **Law of One Price** by using Big Mac prices across countries to infer **Purchasing Power Parity (PPP)** exchange rates and assess whether currencies appear **overvalued or undervalued** relative to the U.S. dollar.

### Methodology  
- **Assembled the dataset** from *The Economist*’s **2015 Big Mac Index** figures, manually structuring country-level observations into a clean, analysis-ready table.  
- **Computed Implied PPP exchange rates** by comparing local Big Mac prices to the U.S. price benchmark (i.e., the exchange rate that would equalize Big Mac prices across countries).  
- **Measured currency misalignment** by calculating the percentage difference between the implied PPP rate and the prevailing market exchange rate, interpreting results as **overvaluation** (currency stronger than PPP) or **undervaluation** (currency weaker than PPP).  

### Key Findings  
- The results indicate meaningful **departures from PPP**, consistent with the idea that identical goods can trade at different effective prices across countries due to frictions such as taxes, trade costs, wages, and market segmentation.  
- **[Insert your finding]**: For example, I found that the **Norwegian Krone was overvalued by X%** against the U.S. dollar, implying that—relative to the PPP benchmark—the Krone’s market value made Norway’s Big Mac price appear high in USD terms.  
- These misalignments suggest that **arbitrage is limited** in practice: even when price gaps imply potential profit opportunities, real-world constraints prevent the rapid equalization of prices that the Law of One Price would predict.  


## Contact

If you’re interested in my work or would like to connect about opportunities in **[Data Analysis / Economic Consulting / Finance]**, feel free to reach out via GitHub or LinkedIn.
```

Assignment 1:

# The Cost of Living Crisis: A Data-Driven Analysis

---

## The Problem

Why the "average" CPI fails students.

The official Consumer Price Index (CPI) uses a national average weighting system designed for typical American households. However, **students are not typical consumers**—their spending patterns diverge dramatically from the national baseline.

**The disconnect:**
- **Tuition:** CPI weight = 3% | Student reality = 40% (**+37 percentage points**)
- **Rent:** CPI weight = 18% | Student reality = 30% (**+12 percentage points**)
- **Food & Entertainment:** CPI weight = 19% | Student reality = 30% (**+11 percentage points**)

When tuition rises 29% and rent rises 50%, these shocks devastate student budgets. Yet because tuition has only a 3% weight in the CPI, its explosive growth barely registers in official inflation figures.

**Result:** When policymakers report "inflation is 2-3%," students are actually experiencing 5-6% or higher. Official statistics systematically underestimate student economic pressure.

---

## Methodology

Python, APIs, and Index Theory (mentioning Laspeyres).

**Tech Stack:**
- **Python** - Data processing and analysis
- **Pandas** - Time series manipulation
- **Matplotlib** - Visualization
- **fredapi** - Federal Reserve Economic Data API
- **Statsmodels** - Statistical validation

**Theoretical Foundation: Laspeyres Index**

Applied the **Laspeyres Price Index**, the same framework used by the Bureau of Labor Statistics for the official CPI.

**Formula:**
```
Index = Σ(P_current × Q_base) / Σ(P_base × Q_base) × 100
```

Where P = price, Q = quantity weight, base period = January 2016.

**Pipeline:**

1. **Assembled the dataset** from manual collection (tuition, rent, Chipotle, Spotify) and FRED API proxies (CUSR0000SEEB for tuition, CUSR0000SEHA for rent, CUSR0000SEFV for food away, CUSR0000SERA02 for streaming).

2. **Computed normalized indices** by re-indexing all series to January 2016 = 100, eliminating "scale fallacy" from different base years (e.g., tuition base = 1982-1984, streaming base = 2002).

3. **Constructed Student SPI** using the Laspeyres formula with student-specific weights:
   - Tuition: 40%
   - Rent: 30%
   - Food Away: 15%
   - Streaming: 15%

4. **Measured currency misalignment** by comparing three inflation dimensions: National CPI, Boston Area CPI (CUSR0000SA0), and Student SPI to quantify geographic and demographic gaps.

---

## Key Findings

"My analysis reveals a **15.2 percentage point divergence** between Student Costs and National Inflation."

**Core Results (January 2016 - December 2024):**

```
National CPI:     +23.5%
Boston CPI:       +27.2%
Student SPI:      +38.7%

Gap Analysis:
├─ Student vs National:  +15.2 pp
├─ Student vs Boston:    +11.5 pp
└─ Boston vs National:   +3.7 pp
```

**Translation:** If official CPI shows 23.5% inflation, students experience 38.7%—a **65% higher burden** than the national average.

**Finding 1:** The results indicate meaningful **departures from PPP**, consistent with the idea that identical goods can trade at different prices across groups.

- **Tuition** (40% of student spending, 3% of CPI): +28.9% growth
- **Rent** (30% of student spending, 18% of CPI): +50.0% growth in Boston
- **Food Away** (15% of student spending): +53.3% growth

**Finding 2:** Geographic variation amplifies pressure. Boston students face a **double hit**: regional inflation (+3.7 pp above national) compounded by student spending structure (+11.5 pp above Boston average).

**Finding 3:** These misalignments suggest that **arbitrage is limited** in practice: even when price gaps imply potential profit opportunities (cheaper national CPI basket vs. expensive student basket), structural factors (locked-in tuition contracts, local housing markets, time constraints driving food choices) prevent convergence.

**Interpretable result:** Students don't just "feel" poorer—they are objectively experiencing 15+ percentage points more inflation than official statistics suggest, driven by structural misalignment between CPI weights and student consumption patterns.

---
