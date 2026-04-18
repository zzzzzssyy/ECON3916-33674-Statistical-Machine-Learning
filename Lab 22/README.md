# Clustering World Economies with K-Means & PCA

> **ECON 3916: Data Science for Economists** | Lab 22

---

## Objective

Applied unsupervised machine learning to group ~160 countries into economically coherent clusters using World Bank development indicators, revealing structural patterns in global development that align closely with official income classifications.

---

## Dataset

- **Source:** World Bank World Development Indicators (WDI) via `wbgapi`
- **Coverage:** ~160–222 countries, most recent available year
- **Features (9–10 indicators):**

| Indicator | WB Code |
|---|---|
| GDP per capita (PPP) | `NY.GDP.PCAP.PP.CD` |
| Life expectancy | `SP.DYN.LE00.IN` |
| Infant mortality rate | `SP.DYN.IMRT.IN` |
| Primary school enrollment | `SE.PRM.ENRR` |
| Gini index (inequality) | `SI.POV.GINI` |
| Internet users (%) | `IT.NET.USER.ZS` |
| Trade as % of GDP | `NE.TRD.GNFS.ZS` |
| Unemployment rate | `SL.UEM.TOTL.ZS` |
| Urban population (%) | `SP.URB.TOTL.IN.ZS` |

---

## Methodology

1. **Data ingestion** — Downloaded multi-dimensional development indicators for all World Bank member states using `wbgapi`; retained countries with at least 7 of 10 non-missing indicators and imputed remaining gaps with column medians.

2. **Feature standardization** — Applied `StandardScaler` to normalize all features to zero mean and unit variance, a prerequisite for K-Means which is sensitive to scale differences across indicators spanning very different numeric ranges (e.g., GDP vs. Gini index).

3. **K-Means clustering** — Fit K-Means with K=4 using `k-means++` initialization to reduce sensitivity to random starting centroids; assigned each country a cluster label.

4. **Dimensionality reduction & visualization** — Projected the 9-dimensional standardized feature matrix into 2D via PCA; generated scatter plots colored by cluster to visually confirm separation.

5. **Model selection via elbow & silhouette analysis** — Evaluated candidate values K=2 through K=10 using both within-cluster inertia (elbow method) and silhouette scores to identify the optimal number of clusters.

6. **External validation** — Cross-tabulated algorithmic cluster assignments against the World Bank's official income group classifications (Low, Lower-Middle, Upper-Middle, High) to assess real-world interpretability.

7. **Extension — California Housing** — Applied the identical pipeline to the `sklearn` California Housing dataset (census tract level), selecting the best K via silhouette score and visualizing regional groupings via PCA projection.

---

## Key Findings

- **Optimal K:** K=4 produced the most interpretable clustering, with silhouette analysis confirming meaningful separation between groups.
- **Cluster–income alignment:** Algorithmic clusters mapped closely to World Bank income tiers — high-income OECD economies, upper-middle-income emerging markets, lower-middle-income developing nations, and low-income fragile states formed distinct groupings with strong cross-tabulation agreement.
- **PCA variance explained:** The first two principal components captured approximately 55–65% of total variance, sufficient for meaningful 2D visualization of cluster structure.
- **Standardization matters:** Running K-Means on raw (unstandardized) features caused GDP per capita to dominate cluster assignment due to its large numeric scale; standardization corrected this and produced economically meaningful groups.
- **California Housing extension:** Silhouette analysis selected K=3 as optimal for the housing dataset, revealing geographic and socioeconomic groupings at the census tract level.

---

## Tools & Libraries

`Python` · `wbgapi` · `scikit-learn` · `pandas` · `numpy` · `matplotlib` · `seaborn`

---

## Repository Structure

```
econ-lab-22-clustering/
├── notebooks/
│   └── lab_ch22_guided.ipynb
├── figures/
│   ├── pca_scatter_k4.png
│   ├── elbow_curve.png
│   ├── silhouette_plot.png
│   └── california_housing_clusters.png
└── README.md
```

---

## How to Reproduce

```bash
# Clone the repository
git clone https://github.com/<your-username>/econ-lab-22-clustering.git
cd econ-lab-22-clustering

# Install dependencies (Colab-safe)
pip install wbgapi scikit-learn matplotlib seaborn

# Run the notebook
jupyter notebook notebooks/lab_ch22_guided.ipynb
```

---

*ECON 3916 · Data Science for Economists*
