# # 🛒 India Q-Commerce Dark Store EDA (2015–2025)
### From Dunzo's Bengaluru-only Origins to Blinkit's 50%+ Market Dominance

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=flat&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.x-3F4F75?style=flat&logo=plotly&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat&logo=mysql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-2ea44f?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

---

## 🎯 Project Overview
An end-to-end data analytics project on **1 crore (10,000,000) Q-Commerce orders** across 11 years (2015–2025) and 7 apps — combining Python EDA and SQL analytics, both calibrated against verified real-world facts rather than plausible-looking synthetic patterns.

Two rounds of fact-checking against actual industry history were applied to the dataset:
1. **City tier expansion** — corrected against Dunzo's real company history (Bengaluru-only through 2016; genuine Tier 2/3 push only began in 2021 with Blinkit/Zepto's dark-store model)
2. **COVID-19 impact** — corrected to show a real Mar–Jun 2020 lockdown order-volume spike, not flat noise

## 📓 Notebooks — Two-Part Analysis

| Notebook | Purpose |
|---|---|
| **`notebooks/DarkStore_QCommerce_EDA_Project.ipynb`** | Full Python EDA — 12 phases, cleaning, feature engineering, univariate/time-series/geographic/behavioural analysis, 20+ charts (Matplotlib/Seaborn/Plotly) |
| **`notebooks/02_SQL_Analytics.ipynb`** | Python + MySQL integration — 33 SQL queries (Basic → Intermediate → Advanced → Validation) run directly from Jupyter via `sqlalchemy` + `pymysql`, results rendered as DataFrames inline |

The SQL notebook is a **companion**, not a duplicate — it validates the same real-world corrections (city tier, COVID spike) using pure SQL (`RANK`, `DENSE_RANK`, `NTILE`, `LAG`, CTEs, rolling windows) and adds RFM-style / promo-effectiveness / MNAR-proof queries on top.

## ❓ Problem Statement
1. How did Dunzo's real single-city origin (2015) evolve into a 7-app, pan-India category?
2. Did COVID-19 actually spike Q-Commerce orders — and can that be proven in the data?
3. How did payment habits shift from 82% Cash-on-Delivery (2015) to 58% UPI (2025)?
4. How did app market share evolve from a Dunzo monopoly to Blinkit's 50%+ dominance?
5. Can the same real-world patterns be independently verified via SQL, not just Python?

## 📁 Dataset
| File | Rows | Notes |
|---|---|---|
| `qcommerce_orders_2015.csv` → `_2025.csv` | 1,00,000 → 25,00,000 | One file per year | 
| **Total** | **1,00,00,000 rows** | 36 columns |

> 📦 **Data not included in this repo** (total size 2.29 GB, exceeds GitHub's 100MB/file limit). Download from: **[ADD YOUR KAGGLE/DRIVE LINK HERE]**

### Key Columns
`order_id` · `date/year/month/day/hour` · `app` · `city` · `city_tier` · `category` · `order_amount_rs` · `discount_rs` · `payment_mode` · `delivery_slot` · `delivery_time_min` · `order_status` · `customer_rating` · `customer_lifetime_orders` · `days_since_last_order` · `promo_code_used` · `estimated_delivery_distance_km`

### ✅ Real-World Calibration (Verified)
| Fact | Source-backed detail |
|---|---|
| Dunzo launched Bengaluru-only | 2015–2016 = 100% Tier 1 in the data |
| Real Tier 2/3 expansion timing | Only begins meaningfully in 2021 (Blinkit/Zepto dark-store push), reaching 42% by 2025 |
| COVID-19 lockdown spike | Mar–Jun 2020 shows genuine order surge vs Jan–Feb baseline |
| UPI didn't exist in 2015 | 0% UPI share until launch (Apr 2016) |
| App market share evolution | Dunzo monopoly (2015-18) → Amazon Fresh/Instamart entry → 2021 "Big Bang" (Blinkit+Zepto+BBNow) → Blinkit 50%+ by 2025 |
| Payment mode shift | COD 82%→20%, UPI 0%→58% (2015→2025) |

### 🧹 Null Value Handling (8 columns — all 3 missingness types)
| Column | Type | Handling |
|---|---|---|
| `discount_rs`, `delivery_time_min`, `promo_code_used` | MCAR | Simple/group-median fillna |
| `cancel_return_reason`, `customer_lifetime_orders`, `days_since_last_order` | MAR | Logical fillna based on related column |
| `customer_rating`, `estimated_delivery_distance_km` | MNAR | Flag column created first, then group-median fillna |

## 🗂️ Repo Structure
```
qcommerce-darkstore-eda/
├── notebooks/
│   ├── DarkStore_QCommerce_EDA_Project.ipynb   ← Python EDA (12 phases)
│   └── 02_SQL_Analytics.ipynb                   ← SQL + Python (33 queries, MySQL)
├── outputs/          ← 33 SQL query results (CSV), auto-generated on run
├── visuals/          ← charts saved from the EDA notebook
├── data/             ← place downloaded CSVs here (gitignored)
├── README.md
├── requirements.txt
└── .gitignore
```

## 🚀 How to Run

### EDA Notebook
```bash
git clone https://github.com/YOUR_USERNAME/qcommerce-darkstore-eda.git
cd qcommerce-darkstore-eda
pip install -r requirements.txt

# Download the 11 CSVs from the link above into data/
# Open the EDA notebook and set DATA_PATH in Phase 2
jupyter notebook notebooks/DarkStore_QCommerce_EDA_Project.ipynb
```

### SQL Analytics Notebook (MySQL)
```bash
# 1. Install MySQL Server locally (or use an existing instance)
# 2. Open notebooks/02_SQL_Analytics.ipynb
# 3. Phase 1 runs ONCE — loads all 11 CSVs into a MySQL database
# 4. Update MYSQL_USER / MYSQL_PASSWORD / DATA_PATH at the top of Phase 1
# 5. Phase 2 onward can be re-run any time — connects and queries directly
jupyter notebook notebooks/02_SQL_Analytics.ipynb
```

## 🛠️ Tech Stack
`pandas` · `numpy` · `matplotlib` · `seaborn` · `plotly` · `jupyter` · `sqlalchemy` · `pymysql` · MySQL 8.0

## 👤 Author
**Shubham Patil** — Data Science & Analytics
📧 shubhampatil752002@gmail.com · 🔗 linkedin.com/in/shubham-patil-340aa5272 · 🐙 github.com/shubhampatil75

## 📜 License
MIT License — see [LICENSE](LICENSE)

---
*⭐ Star this repo if you found it useful!*
