# 📊 Jolliman Sales Analytics Platform

> **AI-assisted sales analytics pipeline with automated ETL, customer segmentation, and natural-language business insights**

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL%20%2F%20BigQuery-orange.svg)](https://www.postgresql.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange.svg)](https://scikit-learn.org)
[![Claude AI](https://img.shields.io/badge/AI-Claude%20API-purple.svg)](https://anthropic.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📌 Overview

End-to-end sales analytics platform for a multi-channel retail business operating across **e-commerce, retail, and wholesale** channels.

Combines traditional SQL-based reporting with Python automation and AI-assisted interpretation to deliver faster, more reliable business intelligence.

**Key outcomes delivered:**
- ⏱️ **15+ hours/week** of manual processing eliminated through ETL automation
- 🎯 **Customer segmentation** enabling targeted marketing campaigns
- 📈 **Real-time performance dashboards** across all three sales channels
- 🤖 **AI-generated insights** from structured sales data using Claude API

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│              JOLLIMAN SALES ANALYTICS ARCHITECTURE                │
├──────────────────────────────────────────────────────────────────┤
│                                                                    │
│  Data Sources                                                     │
│  ┌────────────┐  ┌────────────┐  ┌─────────────┐                │
│  │ E-Commerce │  │   Retail   │  │  Wholesale  │                │
│  │  Orders    │  │   POS      │  │   B2B CRM   │                │
│  └─────┬──────┘  └─────┬──────┘  └──────┬──────┘               │
│        └───────────────┴─────────────────┘                       │
│                              │                                    │
│                              ▼                                    │
│              ┌───────────────────────────┐                       │
│              │   ETL Pipeline (Python)   │                       │
│              │   Extract → Validate      │                       │
│              │   Transform → Load        │                       │
│              └──────────────┬────────────┘                       │
│                             │                                     │
│               ┌─────────────┼──────────────┐                    │
│               ▼             ▼              ▼                     │
│        ┌────────────┐ ┌──────────┐ ┌────────────┐              │
│        │ SQL Report │ │ Customer │ │  AI Insight│              │
│        │  Library   │ │  Segment │ │  Generator │              │
│        │ (6 queries)│ │ (KMeans) │ │ (Claude AI)│              │
│        └────────────┘ └──────────┘ └────────────┘              │
│               │             │              │                     │
│               └─────────────┴──────────────┘                    │
│                             │                                    │
│                             ▼                                    │
│              ┌───────────────────────────┐                      │
│              │    Business Dashboard     │                      │
│              │    (Plotly / Power BI)    │                      │
│              └───────────────────────────┘                      │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
jolliman-sales-analytics/
│
├── data/
│   └── generate_data.py          # Synthetic multi-channel sales data generator
│
├── sql/
│   └── analytics_queries.sql     # Core SQL reporting library (6 production queries)
│
├── pipeline/
│   └── etl_pipeline.py           # Automated ETL with validation & data quality checks
│
├── segmentation/
│   └── customer_segmentation.py  # ML customer segmentation (RFM + KMeans)
│
├── ai_analysis/
│   └── ai_insights.py            # AI-assisted insight generation via Claude API
│
├── results/                      # Generated reports and visualisations
├── requirements.txt
└── README.md
```

---

## 🔄 ETL Pipeline

### Features
- **Multi-source extraction**: e-commerce, retail POS, wholesale CRM
- **Data validation**: null checks, duplicate detection, range validation, type enforcement
- **Enrichment**: date features, revenue bands, customer joining, margin calculations
- **Data lineage**: row hashing, ETL timestamps, run logs (JSON)
- **Output**: enriched orders, monthly summaries, customer feature tables

### Validation Rules

| Check | Action |
|---|---|
| Null critical fields | Reject row |
| Duplicate order IDs | Reject duplicates |
| Negative revenue | Reject row |
| Future order dates | Reject row |
| Invalid channel value | Reject row |
| Quantity out of range | Warning |

---

## 📊 SQL Analytics Library

Six production-ready queries covering:

| Query | Purpose |
|---|---|
| Monthly Revenue Summary | KPI tracking with MoM growth |
| YoY Comparison | Year-over-year performance by month |
| Product Catalogue Performance | Revenue quartiles + product tiering |
| Customer RFM Base | Recency, Frequency, Monetary scoring |
| Campaign Performance | Attribution and ROI by channel |
| Automated Weekly Digest | Executive summary — replaces manual report |

---

## 👥 Customer Segmentation

**Method:** RFM feature engineering + KMeans clustering with silhouette-optimised k

**Features used:**
- Recency (days since last order)
- Frequency (order count)
- Monetary value (total spend)
- Average order value
- Return rate
- Channel diversity
- Order frequency per month

**Output segments:**

| Segment | Description | Recommended Action |
|---|---|---|
| 🏆 Champions | High RFM, recent, frequent | Reward & upsell |
| ❤️ Loyal Customers | Regular, mid-high value | Loyalty programme |
| 🌱 Recent Customers | New, low frequency | Onboarding flow |
| ⚠️ At-Risk Customers | Haven't bought recently | Win-back campaign |
| 💤 Low-Value Customers | Low spend, infrequent | Reactivation offer |
| 🌟 Potential Loyalists | Promising but inconsistent | Targeted nurturing |

---

## 🤖 AI-Assisted Insights

Uses **Claude AI API** to generate natural-language business commentary from structured data summaries:

- **Performance insights** — trend analysis, growth drivers, risk flags
- **Campaign analysis** — effectiveness scoring and budget recommendations
- **Segment recommendations** — per-segment marketing actions

```python
from ai_analysis.ai_insights import AIInsightGenerator

generator = AIInsightGenerator()  # Set ANTHROPIC_API_KEY env var
results = generator.run_full_analysis(orders_df, segments_df)
print(results["performance"])
```

> ⚠️ API key required for AI features. All other modules work without it.

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/gholibeikadeleh20/jolliman-sales-analytics.git
cd jolliman-sales-analytics
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Generate sample data
```bash
python data/generate_data.py
```

### 4. Run the ETL pipeline
```bash
python pipeline/etl_pipeline.py
```

### 5. Run customer segmentation
```bash
python segmentation/customer_segmentation.py
```

### 6. Generate AI insights (requires API key)
```bash
export ANTHROPIC_API_KEY="your-key-here"
python ai_analysis/ai_insights.py
```

---

## 👩‍💻 Author

**Adeleh Jafargholi Beik, PhD**  
Senior Data Analyst & Data Engineer | Birmingham, UK  
[LinkedIn](https://linkedin.com/in/adeleh-gholibeik-9049907b) | [GitHub](https://github.com/gholibeikadeleh20)

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.
