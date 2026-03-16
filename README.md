# Distress Risk Language in AMD 10-K Filings

## Project Overview

This project investigates whether distress-related language disclosed in **AMD’s 10-K Item 1A (Risk Factors)** increases before periods of stock price decline.

Using a retrieval-based text analysis pipeline, we extract and analyze distress signals from AMD's annual 10-K filings between **2011 and 2024**. These textual signals are transformed into quantitative **distress indices**, which are then tested against subsequent **abnormal stock returns**.

The objective is to examine whether forward-looking risk disclosures contain signals that anticipate future financial deterioration or stock underperformance.

The full methodology and empirical analysis are documented in the project report located in the `report/` folder.



---

# Methodology Overview

The analysis pipeline consists of the following stages:

1. **Data Collection**
   - AMD 10-K filings (2011–2024)
   - AMD total return index
   - S&P 500 benchmark index

2. **Text Processing**
   - Extract Item 1A (Risk Factors)
   - Clean SGML and HTML content
   - Apply sliding-window chunking

3. **Retrieval Layer**
   - Build TF-IDF representations
   - Retrieve top-k relevant chunks using cosine similarity

4. **Distress Index Construction**
   - Define query families: Hard, Soft, Operational
   - Compute chunk-level similarity scores
   - Construct indices using **Coverage × Intensity**

5. **Market Tests**
   - Compute forward abnormal returns (6M / 12M)
   - Evaluate associations using:
     - Spearman correlation
     - Median split comparison
     - OLS regression

---

# Distress Index Types

Three narrative distress indices are constructed:

| Index | Description |
|------|-------------|
| Hard Distress | Severe financial risk signals (default events, covenant violations, restructuring) |
| Soft Distress | Persistent financial pressure signals (losses, liquidity constraints) |
| Operational Distress | Operational uncertainty signals (revenue decline, competitive pressure) |

Only indices constructed in the **global TF-IDF space** are used in the final empirical analysis to ensure cross-year comparability.

---

# Key Findings

- **Soft Distress** shows a negative association with future abnormal returns.
- **Hard Distress** and **Operational Distress** display countercyclical patterns.
- Statistical significance is limited due to the small annual sample size (14 observations).

Overall, softer forms of distress language appear to contain **forward-looking signals of potential stock underperformance**.

---

# How to Reproduce

1. Open the notebook:
[Open the analysis notebook](code/project_code.ipynb)

2. Run all cells sequentially.

The notebook will:

- load the data from `/data`
- construct TF-IDF indices
- compute distress measures
- generate output tables and figures.

---

# Report

The full project report is available here:[Open the report](report/report.pdf)


# Project Contributors

This project was completed as a **group research project**.

- Lingjiang Ji  
- Yingqi Zhao 
- Yuanyi Feng

---
