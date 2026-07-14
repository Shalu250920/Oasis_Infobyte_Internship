# Task 3 · Cleaning Data — Cafe Sales Dataset

Internship task deliverable: a fully documented data-cleaning pipeline that takes a deliberately
messy cafe sales dataset (`dirty_cafe_sales.csv`, 10,000 rows) and turns it into a clean,
analysis-ready dataset (`cleaned_cafe_sales.csv`).

## Contents

| File | Description |
|---|---|
| `Task3_Data_Cleaning.ipynb` | The full, executed Jupyter notebook — data quality report, cleaning steps, and justification for every decision, in markdown cells alongside the code. |
| `dirty_cafe_sales.csv` | Raw input data (place this in the same folder as the notebook). |
| `cleaned_cafe_sales.csv` | Output produced by running the notebook — generated automatically, not included until you run it. |
| `requirements.txt` | Python package versions needed to run the notebook. |
| `README.md` | This file. |

## How to run

1. Make sure `dirty_cafe_sales.csv` is in the **same folder** as `Task3_Data_Cleaning.ipynb`.
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
5. Open `Task3_Data_Cleaning.ipynb` and run all cells (**Run → Run All Cells**).
6. `cleaned_cafe_sales.csv` will be written to the same folder once the notebook finishes.

The notebook has already been executed once end-to-end (all outputs are saved in the `.ipynb`), so
you can also just open and read it without re-running anything if you only want to review the work.

## What's covered

The notebook walks through, in order:

1. **Load & inspect** the raw data.
2. **Data quality report** — nulls, duplicates, dtypes, and value ranges, computed on the raw data.
3. **Uncovering hidden missingness** — the raw file uses the literal strings `"ERROR"` and
   `"UNKNOWN"` as missing-value placeholders (on top of real blank cells), which is why every column
   loads as text initially. These are converted to real `NaN`s first so the rest of the pipeline can
   reason about missingness correctly.
4. **Duplicate removal** — checked and documented (this dataset has none).
5. **Data type correction** — IDs to string, categoricals to `category`, prices/totals to `float`,
   quantity to `int`, dates to `datetime`.
6. **Missing data handling**, done in two layers:
   - **Deterministic derivation first**: the notebook discovers that `Price Per Unit` is a fixed
     function of `Item`, and that `Quantity x Price Per Unit = Total Spent` always holds. Wherever
     two of these three+one fields are known, the rest are reconstructed exactly — no guessing.
   - **Statistical imputation second**, only for what's left: median imputation for `Quantity`, mode
     imputation for `Payment Method`, forward-fill for `Location`, an explicit `"Unknown"` category
     for `Item` where it truly can't be recovered, and row deletion for the small fraction of rows
     with an unrecoverable `Transaction Date`.
   - Every choice is justified in a markdown cell next to the code that implements it.
7. **Outlier detection** via the IQR method on all three numeric columns (none found — documented as
   a deliberate "retain" decision with reasoning, not a skipped step).
8. **Before vs. after summary table** — row count, duplicate count, null count, and dtype accuracy,
   compared side by side.
9. **Save** the cleaned dataset to `cleaned_cafe_sales.csv`, with a reload sanity check.

## Notes / assumptions

- The forward-fill imputation used for `Location` is flagged in the notebook as its weakest-justified
  imputation choice (included primarily to demonstrate the technique on a plausible field); a
  production pipeline might prefer an explicit `"Unknown"` label there too, as was done for `Item`.
- Rows missing `Transaction Date` (~4.6% of the dataset) are dropped rather than imputed, since a
  fabricated date would corrupt any time-based analysis downstream.
