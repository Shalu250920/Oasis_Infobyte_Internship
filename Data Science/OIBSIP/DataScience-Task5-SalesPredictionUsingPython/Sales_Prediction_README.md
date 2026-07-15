# Sales Prediction Using Python

A regression project that predicts product sales based on advertising spend
across TV, Radio, and Newspaper channels, and compares a Linear Regression
baseline against a Random Forest Regressor.

## Objective

Build a regression model that predicts product sales from advertising
budget across different media channels, evaluate model performance, and
determine which advertising channel has the highest impact on sales.

## Dataset

**`Advertising_Budget_and_Sales.csv`** — 200 observations of advertising
spend and resulting sales.

**Columns:**
- `TV Ad Budget ($)` — TV advertising spend
- `Radio Ad Budget ($)` — Radio advertising spend
- `Newspaper Ad Budget ($)` — Newspaper advertising spend
- `Sales ($)` — target variable, product sales

The dataset is clean: no missing values and no duplicate rows.

## Project Structure

```
.
├── Sales_Prediction.ipynb        # Main notebook
├── requirements.txt              # Python dependencies
├── data/
│   └── Advertising_Budget_and_Sales.csv   # Dataset (place here before running)
└── README.md                     # Project documentation
```

## Analysis Workflow

1. **Data loading & cleaning** — null/duplicate checks, descriptive statistics.
2. **EDA** — pairplot of all features, individual scatter plots (Sales vs.
   TV / Radio / Newspaper), correlation matrix heatmap.
3. **Train/test split** — 80/20 split.
4. **Model training:**
   - Linear Regression (baseline)
   - Random Forest Regressor (300 trees)
5. **Evaluation** — MAE, RMSE, and R² for both models.
6. **Residual plot** — for the best-performing model, to check whether
   errors are randomly distributed or systematic.
7. **Interpretation** — which advertising channel drives sales the most,
   using Linear Regression coefficients and Random Forest feature
   importances.

Markdown "Observation" cells sit between each chart, interpreting what the
data and results show.

## Key Findings

- **TV** has the strongest correlation with Sales (r = 0.78), followed by
  **Radio** (r = 0.58). **Newspaper** is the weakest (r = 0.23).
- **Random Forest substantially outperforms Linear Regression**:

  | Model | MAE | RMSE | R² |
  |---|---|---|---|
  | Linear Regression | 1.46 | 1.78 | 0.899 |
  | Random Forest Regressor | 0.61 | 0.74 | **0.983** |

- **TV drives the most overall variation in Sales** (highest correlation
  and highest Random Forest feature importance), but **Radio is the most
  efficient channel per dollar spent** (highest Linear Regression
  coefficient). **Newspaper** contributes the least across every measure.

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
jupyter notebook Sales_Prediction.ipynb
```

## License

This project is open source and available for personal or educational use.
