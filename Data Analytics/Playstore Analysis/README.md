# Unveiling the Android App Market — Google Play Store Analysis

A data analysis of the Google Play Store apps ecosystem: cleaning messy real-world data, exploring app categories, ratings, size, and pricing trends, and running sentiment analysis on user reviews.

## Objective

Perform a comprehensive EDA of the Google Play Store dataset to answer:
- Which app categories are most saturated?
- How are ratings distributed, and do they vary by category?
- Does app size relate to number of installs?
- How do free vs. paid apps compare, and what's the rough revenue picture by category?
- What does user sentiment look like across categories?

## Dataset

- **`googleplaystore.csv`** — ~10,800 Play Store app listings (Category, Rating, Reviews, Size, Installs, Type, Price, Content Rating, Genres, Last Updated, etc.)
- Source: [Google Play Store Apps](https://www.kaggle.com/datasets/lava18/google-play-store-apps) on Kaggle.

**Note on reviews data:** the matching user-reviews file (`googleplaystore_user_reviews.csv`) wasn't available for this project. To keep the sentiment analysis section runnable end-to-end, the notebook **simulates** a review dataset (positive/negative/neutral template reviews, weighted by each app's real rating) and classifies it with VADER. If you have the real reviews file, drop it into this folder and swap it in — the notebook says exactly where in Section 9.

## What's in the notebook

1. Load & inspect the raw data
2. Data quality report (nulls, duplicates, wrong data types)
3. Data cleaning: fix a corrupted row, convert `Installs`/`Price`/`Reviews`/`Size` to numbers, remove duplicates
4. Category analysis — which categories have the most apps
5. Ratings analysis — overall distribution and by category
6. Size vs. installs — is there a correlation?
7. Pricing analysis — free vs. paid split, price distribution, rough revenue estimate by category
8. Sentiment analysis on (simulated) user reviews using VADER
9. Sentiment by category
10. An interactive Plotly bubble chart (size vs. installs vs. rating, by category)
11. Conclusion — 3 takeaways for a developer planning a new app

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Task4_Google_Play_Store_Analysis.ipynb
```

Make sure `googleplaystore.csv` is in the same folder as the notebook before running.

## Tech stack

Python, pandas, numpy, matplotlib, seaborn, plotly, VADER (vaderSentiment)

## Key findings

- `FAMILY`, `GAME`, and `TOOLS` are the most saturated categories — hardest to break into with a generic app.
- App size has almost no correlation with install count.
- Over 90% of apps are free; paid apps are mostly priced under $5.
- `FAMILY`, `GAME`, and `PHOTOGRAPHY` lead in estimated revenue (price × installs, a rough proxy).
