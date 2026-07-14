# Unemployment Analysis with Python — Impact of COVID-19 in India

An exploratory data analysis (EDA) project examining regional and temporal
trends in India's unemployment rate, with a focus on how the COVID-19
pandemic and the March 2020 nationwide lockdown affected employment across
Indian states.

## Objective

Perform EDA on unemployment data to uncover:
- Regional differences in unemployment rates across Indian states
- Month-wise and time-series trends
- The measurable impact of COVID-19 by comparing pre-lockdown vs.
  post-lockdown periods

## Dataset

**[Unemployment in India](https://www.kaggle.com/datasets/gokulrajkmv/unemployment-in-india)**
(`Unemployment_in_India.csv`) — sourced from Kaggle.

- **Coverage:** May 2019 – June 2020 (28 states/union territories)
- **Columns:** Region, Date, Frequency, Estimated Unemployment Rate (%),
  Estimated Employed, Estimated Labour Participation Rate (%), Area
  (Rural/Urban)

This file was chosen over an alternative Kaggle version
(`Unemployment_Rate_upto_11_2020.csv`) because it provides roughly **11
months of pre-COVID data**, enabling a genuine before/after comparison —
the alternative file only had 3 pre-COVID months, which isn't enough for a
meaningful baseline.

## Project Structure

```
.
├── Unemployment_Analysis.ipynb   # Main notebook
├── requirements.txt              # Python dependencies
├── data/
│   └── Unemployment_in_India.csv # Dataset (place here before running)
└── README.md                     # Project documentation
```

## Analysis Workflow

1. **Data loading** — auto-detects and loads CSV(s) from the `data/`
   folder, standardising inconsistent column names/whitespace.
2. **Cleaning** — shape/dtype inspection, null value checks, date parsing,
   and numeric type conversion.
3. **EDA** — region-wise average unemployment rates and month-wise
   national trends.
4. **Time-series chart** — unemployment rate over time for major states
   (Delhi, Maharashtra, Tamil Nadu, and others).
5. **Bar chart** — top 10 states by average unemployment rate.
6. **Correlation heatmap** — relationship between unemployment rate,
   employment, and labour participation rate.
7. **Pre-COVID vs. post-COVID comparison** — data split at 1 April 2020
   (the nationwide lockdown began 25 March 2020), with mean rates
   compared across both periods.
8. **Conclusion** — summary of key findings.

Markdown "Observation" cells sit between each chart, interpreting what the
data shows.

## Key Findings

- **National unemployment rate rose from 9.61% (pre-COVID) to 20.19%
  (post-COVID)** — an increase of roughly 10.6 percentage points.
- **Highest average unemployment:** Tripura (28.35%), Haryana (26.28%),
  and Jharkhand (20.58%).
- **Labour participation fell** from 43.82% to 38.05% post-lockdown, and
  estimated employment dropped by roughly 1.3 million on average.
- Unemployment rate showed little linear correlation with employment or
  labour participation, suggesting the spike was a broad, sudden shock
  rather than a steady structural relationship.

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

1. Download `Unemployment_in_India.csv` from the
   [Kaggle dataset page](https://www.kaggle.com/datasets/gokulrajkmv/unemployment-in-india)
   and place it in a `data/` folder next to the notebook (already included
   if you're using this repo as-is).
2. Launch Jupyter and run all cells:

```bash
jupyter notebook Unemployment_Analysis.ipynb
```

## License

This project is open source and available for personal or educational use.
