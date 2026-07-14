# Iris Flower Classification

A machine learning project that explores the classic Iris dataset and compares
several classification algorithms to predict flower species from petal and
sepal measurements.

## Overview

This notebook walks through a complete, minimal ML workflow:

1. **Load the data** — the Iris dataset via `sklearn.datasets`.
2. **Exploratory Data Analysis (EDA)** — shape, dtypes, null checks, and
   descriptive statistics.
3. **Visualisation** — pairplots and box plots to inspect feature
   distributions across species.
4. **Train/test split** — an 80/20 stratified split.
5. **Model training** — four classifiers trained on the same split:
   - Logistic Regression
   - K-Nearest Neighbours
   - Decision Tree
   - Random Forest
6. **Evaluation** — accuracy, classification reports, and confusion matrices
   for each model.
7. **Model comparison** — a ranked summary of accuracy scores to identify the
   best-performing model.

## Dataset

The [Iris dataset](https://scikit-learn.org/stable/datasets/toy_dataset.html#iris-dataset)
is loaded directly from `scikit-learn` (no external file needed). It contains
150 samples across 3 species (*setosa*, *versicolor*, *virginica*), each with
4 features: sepal length, sepal width, petal length, and petal width.

## Project Structure

```
.
├── Iris_Classification.ipynb   # Main notebook
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation
```

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

Launch Jupyter and open the notebook:

```bash
jupyter notebook Iris_Classification.ipynb
```

Run all cells in order to reproduce the EDA, visualisations, model training,
and evaluation.

## Results

The notebook trains and evaluates four classifiers on a held-out test set and
ranks them by accuracy. Exact scores may vary slightly depending on library
versions, but Logistic Regression, KNN, and Random Forest typically achieve
very high accuracy on this dataset (it is a well-separated, low-noise
classic benchmark).

## License

This project is open source and available for personal or educational use.
