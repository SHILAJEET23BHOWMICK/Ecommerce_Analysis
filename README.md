# E-Commerce Funnel & Retention Analysis
**Tools:** MySQL · Python · Tableau Public  
**Dataset:** Olist Brazilian E-Commerce (Kaggle)  
**Author:** Shilajeet Bhowmick  
**Status:** Completed | 2026

## Business Problem
Olist — Brazil's largest e-commerce marketplace — 
connects small businesses to customers across Brazil. 
With 100,000+ orders across 2 years, three critical 
business questions needed answering:

1. **Where are customers dropping off** in the purchase funnel?
2. **Why are customers not returning** after their first order?
3. **What is driving poor satisfaction scores** in deliveries?
This project builds a complete analytics pipeline — 
from raw messy data across 6 relational tables to an 
interactive business dashboard — answering all three 
questions with real data.

---

## Key Results

| Metric | Value | Business Insight |
|--------|-------|-----------------|
| Total Orders Analyzed | 99,441 | Strong dataset credibility |
| Overall Conversion Rate | 97.16% | Exceptionally healthy funnel |
| Cancellation Rate | 0.62% | Minimal drop-off at ordering stage |
| On-Time Delivery Rate | 92.09% | 7.91% of orders arrive late |
| Avg Review — On Time | 4.21★ | Strong customer satisfaction |
| Avg Review — Late Orders | 2.55★ | 39% satisfaction drop |
| Avg Late Delivery Time | 30.9 days | 3x longer than on-time (10.4 days) |
| Repeat Purchase Rate | 3% | Critical retention gap identified |
| One-Time Buyer LTV | R$212 | Revenue baseline |
| Repeat Buyer LTV | R$468 | 120% higher than one-time buyers |

## 💡 Business Recommendations

**1. Retention is the #1 Priority**
Only 3% of 93,358 customers ever make a repeat purchase.
Yet repeat buyers spend 120% more (R$468 vs R$212 LTV).
→ Implement post-purchase email sequence targeting
  customers at Day 7 and Day 30 after first delivery.
→ Focus on highest AOV first-time buyers first.

**2.Fix Delivery SLA Urgently**
Late deliveries average 30.9 days vs 10.4 days on-time.
This directly causes review scores to drop from
4.21★ to 2.55★ — a 39% satisfaction collapse.
→ Introduce seller penalty system for orders
  exceeding 14-day delivery window.
→ Flag high-risk orders at Day 10 for intervention.

**3.Protect Revenue Concentration Risk**
Top categories drive majority of total revenue.
A stockout in peak season = disproportionate revenue loss.
→ Implement inventory protection policy for
  top 3 categories during Q4 peak season.

**4.Investigate High Cancellation Categories**
Cancellation rate varies significantly across categories.
→ Audit checkout experience and pricing in
  highest-cancellation product segments.

---

## Project Architecture
```
Raw CSV Files (Kaggle — 6 tables, 100K+ rows)
            ↓
Python (Pandas)
→ 5-challenge data cleaning pipeline
→ Feature engineering
→ Cleaned CSVs exported
            ↓
MySQL Database
→ Schema design + table creation
→ Master VIEW joining all 6 tables
→ 10 business KPI queries
→ CTEs, Window Functions, LAG, CASE logic
            ↓
Python (Matplotlib + Seaborn)
→ 10 professional chart exports
→ EDA visualizations
            ↓
Tableau Public
→ 9-sheet interactive dashboard


---

## Data Cleaning — 5 Challenges Resolved

Real-world data is never clean. Here's exactly what
was found and how each issue was resolved:

| # | Challenge | Issue Found | Resolution |
|---|-----------|-------------|------------|
| 1 | Missing Values | 2,965 null delivery timestamps | Flagged as 'not_delivered' — kept in analysis |
| 2 | Wrong Data Types | All 5 timestamps stored as strings | Converted to datetime64 with errors='coerce' |
| 3 | Duplicate Records | Multiple payment rows per order | Aggregated by order_id — not removed |
| 4 | Inconsistent Format | Portuguese category names | Mapped to English, lowercased, stripped |
| 5 | Outliers | Negative payments, impossible dates | Removed errors, flagged genuine outliers |



##  Dashboard — 9 Sheets

| Sheet | Chart Type | Business Question |
|-------|------------|-------------------|
| 1 | Funnel Chart | Where do customers drop off? |
| 2 | Line + Bar | How is revenue trending MoM? |
| 3 | Horizontal Bar | Which categories drive revenue? |
| 4 | Column Chart | Which quarter performs best? |
| 5 | Pie Chart | What % of deliveries are late? |
| 6 | Bar Chart | How does lateness affect reviews? |
| 7 | Bar Chart | Which payment method has highest AOV? |
| 8 | Line Chart | Which cohort retains best? |

<img width="1183" height="586" alt="download" src="https://github.com/user-attachments/assets/f156b775-9a83-4e33-9c8a-f9e399611d61" />



| 9 | Filled Map | Which states generate most revenue? |



