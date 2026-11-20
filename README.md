# ecommerce-analytics
Interactive data analysis and dashboard project exploring 100k+ e-commerce orders (2016–2018). Built with **Python**, **SQL**, **Pandas**, and **Matplotlib**.

---

# Online Shopping Data Analysis Project

## 1. Project Overview
This repository presents a comprehensive end-to-end data analysis project based on the Brazilian E-Commerce public dataset. By examining approximately **100,000 orders** placed between 2016 and 2018 across multiple relational tables (`customers`, `orders`, `order_items`, `payments`, `products`, and `sellers`), this project transforms raw transactional records into visual dashboards, cross-verified SQL/Python solutions, and strategic business recommendations.

---

## 2. Project Objective
* **End-to-End Business Intelligence**: Analyze sales velocity, geographic customer distribution, category revenue concentration, seller rankings, and payment behavior across a multi-year e-commerce ecosystem.
* **Cross-Platform Analytical Validation**: Solve 15 tiered business problems (Basic, Intermediate, and Advanced) in **both SQL and Python**, ensuring 100% numerical parity across both environments.
* **Executive Storytelling**: Translate complex window functions, moving averages, and cohort retention metrics into clear visual dashboards and a side-by-side executive presentation.

---

## 3. Project Requirements
* **Data Architecture & Relational Modeling**: Integrate 6 normalized CSV datasets (`customers`, `orders`, `order_items`, `payments`, `products`, `sellers`) via primary/foreign key relationships (`order_id`, `customer_id`, `product_id`, `seller_id`).
* **Tiered Analytical Problem Solving**:
  * *Basic*: Unique customer cities, annual order counts (2017), category-level revenue, installment payment share, and state-wise customer distribution.
  * *Intermediate*: Monthly order trends (2018), city-level average basket size, category revenue share, price-vs-demand correlation, and seller revenue ranking.
  * *Advanced*: Customer order moving averages, monthly cumulative sales per year, year-over-year (YoY) growth rates, 6-month customer retention rate, and top 3 highest-spending customers per year.
* **Deliverables**: Clean SQL scripts, reproducible Google Colab notebook, dashboard visualizations, and a side-by-side comparison PowerPoint presentation (`Executive_summary_&_Insights.pptx`).

---

## 4. Tools & Technologies Used
* **Programming & Query Languages**: Python 3, SQL (MySQL)
* **Data Manipulation & Analysis**: Pandas, NumPy
* **Data Visualization**: Matplotlib, Seaborn
* **Development & Reporting Environments**: Google Colab, MySQL Workbench, Microsoft PowerPoint, Git/GitHub
* **Core Analytical Techniques**: Multi-table `JOIN`s, Common Table Expressions (CTEs), Window Functions (`SUM() OVER`, `AVG() OVER`, `LAG()`, `DENSE_RANK()`, `ROW_NUMBER()`), Date/Time cohort filtering, and Pearson/Spearman correlation analysis.

---

## 5. Repository Structure
```text
ecommerce-analytics/
│
├── data/                       # Full relational e-commerce dataset
│   ├── customers.csv
│   ├── orders.csv
│   ├── order_items.csv
│   ├── payments.csv
│   ├── products.csv
│   └── sellers.csv
│
├── notebooks/                  # Google Colab Python analysis & visualizations
│   └── onlineshopping.ipynb
│
├── dashboard_Screenshots/      # Visual dashboard outputs
│   ├── Dashboard1.png
│   └── Dashboard2.png
│
├── Presentation/               # Executive summary & side-by-side PPT
│   └── Executive_summary_&_Insights.pptx
│
├── SQL/                        # Basic, Intermediate & Advanced SQL queries
│   └── SQL_script.sql
│
└── README.md                   # Project documentation
```

---

## 6. Challenges Faced & How They Were Resolved
1. **Timestamp Precision & Date Parsing Discrepancies**:
   * *Challenge*: Importing `orders.csv` into SQL truncated timestamp seconds (`:00`), whereas Python retained exact second-level precision, causing minor discrepancies in same-minute repeat order counts during retention analysis.
   * *Resolution*: Standardized datetime casting (`CAST(... AS DATETIME)` in SQL and `pd.to_datetime()` in Python) and aligned tie-breaking rules using `order_id` so both platforms produced identical outputs.
2. **Multi-Row Payment Granularity**:
   * *Challenge*: Orders split across multiple payment methods (e.g., voucher + credit card) inflated row-level counts when calculating installment percentages.
   * *Resolution*: Replaced row counts with distinct order counts (`COUNT(DISTINCT order_id)` in SQL and `.nunique()` in Python) to accurately measure order-level installment usage (`51.46%`).
3. **Customer Identifier Nuances (`customer_id` vs. `customer_unique_id`)**:
   * *Challenge*: The dataset generates a new `customer_id` per order (`99,441` unique IDs), while `customer_unique_id` (`96,096` unique individuals) tracks true repeat buyers across time.
   * *Resolution*: Documented both schemas clearly—using `customer_unique_id` for true behavioral retention (`~2.32%`) and `customer_id` (`0.00%`) where order-level isolation was required.
4. **Floating-Point Tie Handling in Rankings**:
   * *Challenge*: Minor floating-point precision differences in Pandas affected `DENSE_RANK()` ties for top spenders in 2016.
   * *Resolution*: Converted monetary values to integer cents before ranking in Python to match SQL's `ROUND(..., 2)` behavior identically.

---

## 7. Key Insights Discovered
1. **Exponential Year-over-Year Revenue Scaling**:
   * Platform sales accelerated rapidly in 2018, surpassing **7 Million BRL by August 2018** and hitting cumulative revenue milestones months ahead of 2017's trajectory.
2. **High Category Revenue Concentration**:
   * **Health & Beauty** (`beleza_saude`) leads all categories with **~9.3%–9.4% of total revenue**, followed closely by *Watches & Gifts* (`relogios_presentes`). The top 10 categories generate over **63%** of total marketplace sales.
3. **Zero Price Elasticity of Demand**:
   * Statistical testing between product price and purchase frequency yielded a near-zero correlation (Pearson: `-0.032`, Spearman: `-0.064`), proving that lower prices alone do not drive higher order volume.
4. **Severe Customer Retention Bottleneck**:
   * Over **97%–98% of customers are one-time buyers**, with a 6-month repeat purchase rate of only **~1.88%–2.32%** (and **0.00%** at the per-order `customer_id` level).
5. **Installment Payment Adoption & Geographic Concentration**:
   * **51.46% of orders** utilize multi-installment payments, while customer demand is heavily concentrated in southeastern states led by **São Paulo (SP)** with **41,746 customers**.

---

## 8. Recommendations for Business Improvement
* **Launch Post-Purchase Retention Campaigns**: Address the ~98% single-purchase drop-off by introducing automated email/SMS win-back flows at 30, 60, and 90 days, paired with first-repeat-order discount vouchers inside delivery packages.
* **Shift Seller Strategy from Price Cuts to Service Quality**: Because price reductions show negligible impact on sales volume, guide sellers to invest in faster shipping, accurate product descriptions, and higher review ratings rather than margin-eroding price wars.
* **Double Down on High-Performing Categories & Regions**: Allocate prime homepage visibility and seasonal ad spend to top-performing categories (*Health & Beauty*, *Watches & Gifts*, *Bed, Bath & Table*) while expanding fulfillment hubs outside São Paulo (SP) to reduce delivery times and unlock growth in emerging states.
* **Promote Flexible Installment Plans on High-Ticket Items**: Since more than half of all orders rely on installments, highlight interest-free installment tiers on mid-to-high-priced products to boost average order value (AOV).
* **Scale Infrastructure Ahead of Peak Seasons**: Prepare cloud capacity, payment gateways, and seller onboarding pipelines in Q1/Q2 to support compounding mid-year transaction surges.

---

## 9. How to Run the Project Locally
1. **Clone the repository**:
   ```bash
   git clone https://github.com
   ```
2. **Run the Python Notebook**:
   * Open `notebooks/onlineshopping.ipynb` in **Google Colab** or Jupyter Notebook.
   * Ensure the 6 dataset files from `data/` are uploaded to your working directory and click **Run All** to execute the queries and generate the dashboard visuals.
3. **Run the SQL Scripts**:
   * Import the CSV files from `data/` into MySQL (or any relational database) and execute `SQL/SQL_script.sql` to reproduce all 15 query outputs.
