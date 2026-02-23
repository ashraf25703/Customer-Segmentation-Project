# Customer Segmentation Using K-Means Clustering

**Author:** Md Ashraf Khan

## Overview

This project applies **RFM (Recency, Frequency, Monetary) analysis** combined with **K-Means clustering** to segment customers into actionable behavioral groups. The goal is to increase repeat purchases and reduce churn by identifying distinct customer profiles and tailoring marketing strategies to each.

---

## Analytical Framework

| Dimension  | Captures                    | Business Signal            |
|------------|-----------------------------|----------------------------|
| **Recency**    | Days since last purchase    | Engagement & interest      |
| **Frequency**  | Unique orders placed        | Loyalty & habit            |
| **Monetary**   | Total spend                 | Customer lifetime value    |

---

## Dataset

- **Source:** `Online Retail.xlsx`
- A transactional retail dataset containing customer orders, invoice dates, quantities, and unit prices.

---

## Project Structure / Notebook Sections

1. **Imports & Visual Style** — Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`
2. **Load Data** — Read raw Excel file
3. **Initial Inspection** — Data types, nulls, summary statistics
4. **Data Cleaning** — Four rules applied:
   - Drop rows with no `CustomerID`
   - Remove cancelled invoices (prefix `C`)
   - Remove rows with non-positive `Quantity`
   - Remove rows with non-positive `UnitPrice`
5. **RFM Feature Construction** — Aggregate per customer
6. **Feature Scaling** — `StandardScaler` to normalize RFM dimensions
7. **Optimal k — Elbow Method + Silhouette Score** — Evaluated k from 2–9
8. **Final KMeans Model (k = 4)** — Validated by both elbow inflection and highest silhouette score
9. **Rule-Based Segment Labels** — Map clusters to human-readable segments using RFM quantile thresholds
10. **Cluster × Segment Summary**
11. **Visualisation 1** — Segment distribution
12. **Visualisation 2** — RFM distribution by segment
13. **Visualisation 3** — Radar/spider chart (RFM dimensions per segment)
14. **Visualisation 4** — Recency vs. Monetary scatter by segment
15. **Business Interpretation & Recommendations**
16. **Conclusion**

---

## Customer Segments

### 🟣 VIP — High-Value Champions
Top-quartile spenders who purchased recently. Recommended action: invitation-only loyalty tier with early product access and personalised rewards.

### 🩷 Loyal — Frequent Buyers with Moderate Spend
Regular shoppers with narrow category focus. Recommended action: cross-sell via 'Complete the Set' bundles targeting adjacent product categories.

### 🟡 At Risk — Previously Engaged, Now Drifting
High recency (long since last purchase) but historically active. Recommended action: 3-step win-back email sequence with a time-limited offer.

### 🩵 New — Recent First-Timers
Low frequency, likely first or second purchase. Recommended action: onboarding email sequence within 48 hours of first purchase, avoiding heavy discounts.

---

## Key Takeaways

- **k = 4** was selected based on both the elbow method and highest silhouette score.
- RFM segmentation enables **budget reallocation** — concentrating retention spend on At Risk customers and upsell spend on Loyals improves marketing ROI without increasing total spend.
- The model should be **refreshed monthly**, and segment migration rates should become a core marketing KPI.

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
openpyxl
```

Install with:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

---

## Usage

1. Place `Online Retail.xlsx` in the same directory as the notebook.
2. Open the notebook and run all cells sequentially.
3. Review the visualisations and business recommendations in sections 11–16.
