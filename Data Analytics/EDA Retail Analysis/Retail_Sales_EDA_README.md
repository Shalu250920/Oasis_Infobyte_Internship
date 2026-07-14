# EDA on Retail Sales Data

An exploratory data analysis project on an order-level retail sales dataset,
uncovering time-series trends, product and category performance, regional
patterns, and actionable business recommendations.

## Objective

Perform a thorough Exploratory Data Analysis on a retail sales dataset to
uncover patterns, customer behaviour trends, and actionable business
insights.

## Dataset

**`train.csv`** — 9,800 retail orders placed between **2015 and 2018**
(based on the classic Superstore sales dataset).

**Columns:** Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer
ID, Customer Name, Segment, Country, City, State, Postal Code, Region,
Product ID, Category, Sub-Category, Product Name, Sales.

> **Note:** this dataset does not include customer `Age` or `Gender`
> columns. The customer-behaviour analysis instead uses `Segment`
> (Consumer / Corporate / Home Office) and `Region`, the closest available
> proxies for customer profile in this data — no demographic data is
> fabricated.

## Project Structure

```
.
├── Retail_Sales_EDA.ipynb   # Main notebook
├── requirements.txt         # Python dependencies
├── data/
│   └── train.csv            # Dataset (place here before running)
└── README.md                # Project documentation
```

## Analysis Workflow

1. **Data loading & inspection** — shape, dtypes, null check, duplicate check.
2. **Type conversion & feature engineering** — parses Order/Ship Date,
   derives Year/Month/Quarter/Weekday and shipping delay in days.
3. **Descriptive statistics** — mean, median, mode, std dev for numerical
   columns.
4. **Time series analysis** — monthly and quarterly sales trend line charts.
5. **Customer analysis** — Segment distribution and sales, Region sales.
6. **Product analysis** — top 10 best-selling products by revenue, revenue
   by category.
7. **Correlation heatmap** — Sales, shipping delay, order month/year,
   postal code.
8. **Additional insight** — average order value and shipping delay by ship
   mode, testing whether faster shipping correlates with bigger orders.
9. **Conclusion** — actionable business recommendations.

Markdown "Observation" cells sit after every chart, interpreting what the
data shows.

## Key Findings

- Sales are right-skewed: mean **$230.77** vs. median **$54.49** — a small
  number of high-value orders drive a large share of revenue.
- Clear seasonal pattern: **Q4 sales peak every year** (2015–2018), with a
  consistent upward year-over-year trend.
- **Technology** has the highest total revenue despite the fewest orders
  (highest average order value, ~$456); **Office Supplies** has the most
  orders but the lowest average order value (~$119).
- **West** and **East** regions generate the most sales; **South** trails
  all other regions.
- Shipping speed (Ship Mode) shows **no meaningful relationship** with
  order value (correlation ≈ 0).

## Business Recommendations

1. **Plan inventory/staffing around the confirmed Q4 seasonal peak.**
2. **Investigate and address the South region's underperformance.**
3. **Re-evaluate premium shipping pricing/eligibility**, since faster
   shipping doesn't correlate with higher order value.
4. **Grow average order value in Office Supplies through bundling**, given
   its high volume but low ticket size.

## Getting Started

### Prerequisites

- Python 3.8+

### Installation

```bash
git clone <your-repo-url>
cd <your-repo-folder>
pip install -r requirements.txt
```

### Usage

Launch Jupyter and run all cells:

```bash
jupyter notebook Retail_Sales_EDA.ipynb
```

## License

This project is open source and available for personal or educational use.
