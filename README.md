# ecommerce-analytics
Interactive data analysis and dashboard project exploring 100k+ e-commerce orders. Built with Python, Pandas, and Matplotlib.

# 📊 Online Shopping Data Analysis Project

## 🎯 Project Overview
This repository contains a data analysis project focused on the public e-commerce dataset. By examining approximately **100,000 successful orders** across 2016–2018, this analysis uncovers key business insights regarding sales growth, category performance, pricing elasticity, and customer retention.

This project was built as a structured data analysis assignment to turn raw relational e-commerce tables into clear, actionable business strategies.

---

## 📂 Repository Structure
To keep the workspace clean and organized, the files are structured into separate directories:

```text
ecommerce-analytics/
│
├── data/                  # Contains the full dataset
│   ├── customers.csv
│   ├── orders.csv
│   ├── order_items.csv
│   ├── payments.csv
│   ├── products.csv
│   └── sellers.csv
│
├── notebooks/             # Contains the Google Colab Notebook code
│   └── onlineshopping.ipynb
│
├── dashboard_Screenshots/                
│   └── Dashboard1.png
│   └── Dashboard2.png
|
├── Presentaion/                
│   └── Executive_summary_&_Insights.pptx
|
├── SQL/                
│   └── SQL_script.sql
│
└── README.md              # Project documentation
```

---


## 🛠️ Tech Stack & Key Analytics
* **Language**: Python 3, SQL
* **Libraries**: Pandas, NumPy, Matplotlib
* **Core Techniques**: Multi-table relational joins, data cleaning (filtering canceled/unavailable orders), cumulative window aggregation, and statistical correlation tests (Pearson & Spearman coefficients).

---  
## SQL queries
* **SQL_script.sql** contains different basic, intermediate, advanced queries to analyze data.
----

## 📈 Key Visual Insights

### 1. Cumulative Revenue Profile (Year-over-Year Growth)
* **Insight**: Sales in 2018 scaled exponentially compared to 2017. By August 2018, total platform sales surpassed **7 Million BRL**, hitting performance milestones months ahead of the previous year's schedule. 
* **Business Action**: Infrastructure, server capacities, and seller onboarding programs must scale up dynamically in the first half of the year to match compounding transaction velocities.

### 2. Category Performance (Market Share Concentration)
* **Insight**: **Health & Beauty** is the absolute #1 category on the platform, accounting for **9.4% of all revenue generated**. The top 10 categories alone generate more than **63%** of overall marketplace sales.
* **Business Action**: Allocate premium promotional banners and marketing budgets directly to *Health & Beauty* and *Watches & Presents*, as these categories enjoy guaranteed customer traction and high margins.

### 3. Price vs. Sales Volume (The Price Elasticity Myth)
* **Insight**: Statistical tests yield a correlation score near zero (Pearson: `-0.033`, Spearman: `-0.064`). Lowering an item's price does **not** trigger an organic increase in transaction volume.
* **Business Action**: Sellers should avoid margin-destroying price wars. Instead, keep prices fair and compete on non-price conversion variables like high review scores and fast shipping.

### 4. 6-Month Customer Retention Rate (The Loyalty Gap)
* **Insight**: Company faces an extreme loyalty bottleneck: **98.38%** of shoppers are "One-and-Done" buyers. Only **1.62%** return for a second purchase within 6 months.
* **Insight Context**: Because company operates as a silent backend aggregator on major department store websites, consumers never realize they are buying through whch seller, which limits organic brand stickiness.
* **Business Action**: To fix this "leaky bucket," introduce automated email retargeting or insert physical discount flyers directly inside shipping boxes to encourage repeat sales.

---

## 🚀 How to Run the Project Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com
   ```
2. **Open the Notebook**:
   Navigate to the `notebooks/` folder and open `onlineshopping.ipynb` inside Google colab.
3. **Execute Cells**:
   The notebook is pre-configured to look directly inside the `data/` folder paths. Simply click **Run All** to process the data pipeline and display the 4-panel dashboard visuals.

