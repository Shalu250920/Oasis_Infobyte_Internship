# Task 1 · Predicting House Prices with Linear Regression

Internship task deliverable: an end-to-end Linear Regression workflow — EDA, feature engineering,
encoding, correlation analysis, training, evaluation, and interpretation — applied to
`House_Price_Prediction_Dataset.csv` (2,000 house records).

## Contents

| File | Description |
|---|---|
| `Task1_House_Price_Prediction.ipynb` | The full, executed Jupyter notebook — EDA, feature selection reasoning, encoding, correlation heatmap, model training, evaluation, diagnostic plots, coefficient analysis, and a bonus Ridge/Lasso comparison, all documented in markdown cells alongside the code. |
| `House_Price_Prediction_Dataset.csv` | Raw input data (place this in the same folder as the notebook). |
| `requirements.txt` | Python package versions needed to run the notebook. |
| `README.md` | This file. |

## How to run

1. Make sure `House_Price_Prediction_Dataset.csv` is in the **same folder** as
   `Task1_House_Price_Prediction.ipynb`.
2. Create/activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate      # Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Launch Jupyter Lab:
   ```bash
   jupyter lab
   ```
5. Open `Task1_House_Price_Prediction.ipynb` and run all cells (**Run → Run All Cells**).

The notebook has already been executed once end-to-end (all outputs and plots are saved in the
`.ipynb`), so you can also just open and read it without re-running anything.

## What's covered

1. **Load & EDA** — null check, duplicate check, descriptive statistics, target (`Price`)
   distribution, numeric feature distributions, and categorical-vs-price boxplots.
2. **Feature selection discussion** — a markdown table reasoning through the expected effect of
   each candidate feature (`Area`, `Bedrooms`, `Bathrooms`, `Floors`, `Age`, `Location`,
   `Condition`, `Garage`) before any modelling is done, and why `Id` is excluded.
3. **Missing value handling & encoding** — a defensive median/mode imputation strategy (this
   particular dataset has zero missing values, but the strategy is implemented and documented
   anyway), `YearBuilt` engineered into `Age`, and `Location`/`Condition`/`Garage` one-hot encoded
   with `drop_first=True` to avoid the dummy variable trap.
4. **Correlation heatmap** on the fully-encoded numeric dataframe, with features ranked by
   absolute correlation with `Price`.
5. **80/20 train/test split**.
6. **Linear Regression** trained with scikit-learn.
7. **Evaluation**: MSE, RMSE, and R², plus a "predict the mean" baseline for context.
8. **Actual vs. predicted scatter plot** with a reference diagonal.
9. **Residual plot** (vs. predicted value, and a residual distribution histogram).
10. **Coefficient analysis** — both raw coefficients (interpretable in original units) and
    standardised coefficients (fairly comparable across features of different scales), with a
    horizontal bar chart of feature impact.
11. **Bonus: Ridge vs. Lasso** — both fit on standardised features and compared against Linear
    Regression on MSE/RMSE/R², plus a look at which features Lasso's L1 penalty shrinks to zero.

## An important, honest finding

This particular dataset shows **essentially no linear correlation** between any of the given
features and `Price` (all correlations are near zero), and the resulting Linear Regression model
has an R² close to zero — no better than predicting the average price for every house. The notebook
does not paper over this: Sections 6, 9, 10, 11, 12, and 13 each confirm the same result from a
different angle (correlation, evaluation metrics, prediction plot, residuals, coefficients, and
regularised models) and the concluding section discusses what that means and what a next step would
be in a real project (verify how `Price` was generated, look for additional predictive features, or
try non-linear models). This is intentional — the task asks for genuine model *interpretation*, and
an honest "the signal isn't there" is a more valuable and more defensible interpretation than
overstating a weak result.
