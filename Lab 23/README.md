# FOMC Text Analysis: Sentiment and Clustering

## Overview
This project analyzes Federal Open Market Committee (FOMC) meeting minutes using natural language processing (NLP) techniques. The goal is to understand how the Federal Reserve’s communication changes over time, especially during different economic conditions.

By converting text into data, this project explores sentiment, uncertainty, and structural shifts in how the Fed communicates policy decisions.

---

## Key Questions
- How does the tone of FOMC communication change over time?
- Does sentiment reflect major economic events like crises?
- Can we identify different “communication regimes” using clustering?

---

## Data
- Source: FOMC Meeting Minutes  
- Format: Text documents  
- Time Range: Multiple years (including pre- and post-crisis periods)

---

## Methods

### 1. Text Processing (TF-IDF)
- Converted text into numerical features using TF-IDF  
- Removed extremely common and rare words  
- Focused on meaningful economic language  

### 2. Sentiment Analysis (Loughran-McDonald Dictionary)
- Applied a finance-specific sentiment dictionary  
- Measured positive, negative, and uncertain tone  
- Generated sentiment scores for each meeting  

### 3. Time-Series Analysis
- Plotted sentiment scores over time  
- Compared trends with major economic events  

### 4. Clustering (K-Means)
- Reduced dimensionality using SVD  
- Grouped documents into clusters based on language patterns  
- Identified structural changes in communication  

---

## Key Findings
- Sentiment becomes more negative during economic crises such as 2008 and COVID-19  
- Uncertainty increases during unstable periods and policy transitions  
- Clustering results suggest a clear shift in Fed communication before and after major economic events  
- The Fed’s language evolves over time rather than staying constant  

---

## Conclusion
This project shows that central bank communication is not static. Instead, it responds to economic conditions in a systematic way. By combining NLP and economic intuition, we can better understand how policy signals are communicated to the public.

---

## Tools Used
- Python  
- Pandas  
- Scikit-learn  
- NLP (TF-IDF, sentiment analysis)  
- Matplotlib  

---

## Takeaway
Turning text into data provides a powerful way to study economic policy. Even simple tools like sentiment analysis and clustering can reveal meaningful patterns in how institutions communicate.
