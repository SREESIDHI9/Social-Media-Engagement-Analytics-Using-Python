# Social-Media-Engagement-Analytics-Using-Python
Built with NumPy, Pandas, Matplotlib, Seaborn, and Plotly Express, the workflow takes raw social media interaction data from initial inspection to actionable platform insights. This end-to-end Python analytics project examines a 5,000-record social media engagement dataset.

## Project Overview
Social media platforms generate vast volumes of interaction metrics—such as likes, comments, shares, impressions, and watch time—every day. This project analyzes a social media engagement dataset using Python to clean raw data, engineer meaningful engagement features, explore user and content patterns through statistical summaries and visualizations, and translate analytical insights into actionable content and platform strategies.

## Objective
The primary objective of this assignment is to build an end-to-end exploratory and statistical data analytics workflow in Python to:
* Import, inspect, clean, and standardize a 5,000-record social media dataset.
* Engineer derived metrics (such as engagement score and log-transformed impressions) and perform multi-dimensional aggregations.
* Compute descriptive and distributional statistics across key engagement and audience variables.
* Create visualizations across Matplotlib, Seaborn, and Plotly to uncover content, demographic, behavioral, and sentiment trends.
* Formulate practical business and policy recommendations backed by quantitative findings.

## Dataset Description
* **File Name:** `social_media_engagement_5000.csv`.
* **Dimensions:** 5,000 records across 19 initial columns (expanding to 22 columns after feature engineering)
* **Time Span:** Posts spanning January 1, 2022 through December 31, 2023.
* **Geographic & Audience Coverage:** 10 countries (including India, Canada, Brazil, UAE, USA, France, UK, Australia, Germany, and Japan), 3 standardized gender categories (`Male`, `Female`, `Other`), ages 13–64, verification status (`is_verified`), follower counts, and 3 device types (`mobile`, `tablet`, `desktop`).
* **Content & Engagement Attributes:** `user_id`, `post_id`, `post_type` (`reel`, `image`, `text`, `video`), `post_category` (`fitness`, `tech`, `music`, `education`, `lifestyle`, `travel`, `fashion`, `food`), `likes`, `comments`, `shares`, `watch_time_sec`, `impression_count`, `posted_at`, `sentiment` (`positive`, `neutral`, `negative`), `hashtags`, and `engagement_rate`.
* **Data Quality Profile:** Initial inspection identified 150 missing values each in `age`, `gender`, `likes`, `comments`, `shares`, and `sentiment`, alongside string formatting inconsistencies in `posted_at`, `gender`, and `sentiment`.

## Workflow
1. **Data Import & Setup:** Loaded `social_media_engagement_5000.csv` into a Pandas DataFrame, inspected initial column data types, parsed `posted_at` into `datetime64` (`%d-%m-%Y`), and ran baseline NumPy array operations (`mean`, `max`, `std`) on likes.
2. **Data Cleaning & Feature Extraction:** Detected missing values using `isnull().sum()`, imputed numeric fields (`age`, `likes`, `comments`, `shares`) with medians and categorical fields (`gender`, `sentiment`) with modes, removed duplicate rows, clipped unrealistic/negative interaction values at `0`, standardized `gender` and `sentiment` strings, and extracted `hashtag_count` from `hashtags`.
3. **Exploratory Data Analysis (EDA):** Inspected structure (`head()`, `tail()`, `shape`, `columns`, `info()`, `describe()`), analyzed categorical frequency distributions (`value_counts()`, `nunique()`), computed a numeric correlation matrix, and generated initial `groupby()` aggregations by `post_type` and `country`.
4. **Data Wrangling:** Created `engagement_score` (`likes + comments + shares`) and `log_impressions` (`np.log1p(impression_count)`), and summarized mean engagement metrics across `post_type`, `country`, and `sentiment`.
5. **Statistical Analysis:** Calculated mean, median, mode, standard deviation, variance, 25th/50th/75th percentiles, skewness, and kurtosis for `likes`, `comments`, `shares`, `watch_time_sec`, `engagement_rate`, and `follower_count`.
6. **Data Visualization:** Built visual analyses covering scatter, line, bar, pie, histogram, box, count, violin, pair, correlation heatmap, swarm, and interactive Plotly charts to examine engagement, audience demographics, devices, and sentiment.

## Key Findings
* **Engagement Distribution & Skewness:** Mean likes are `10,107.00` (median `10,105.50`, SD `5,702.29`), while `engagement_rate` is strongly right-skewed (skewness `18.78`, kurtosis `482.99`) with a mean of `0.964` and a median of `0.254` (max `191.504`), driven by low-impression posts achieving high engagement ratios (`impression_count` vs. `engagement_rate` correlation of `-0.232`).
* **Format & Category Performance:** `video` posts achieve the highest average engagement rate (`1.122`) and average likes (`10,188.60`), followed by `text` (`1.065` engagement rate) and `image` (`0.896`), while `fitness` (`675` posts) and `tech` (`665` posts) lead content volume across the 8 categories.
* **Geographic Patterns:** `India` records the highest average impressions (`52,462.39`), whereas `Brazil` (`1.541`) and `Australia` (`1.324`) lead in average `engagement_rate`, and `Australia` (`4,150.68 sec`) and `UK` (`4,118.69 sec`) show the highest average watch times.
* **Sentiment Dynamics:** `positive` posts make up the largest share of content (`2,513` of `5,000` posts), while `negative` sentiment posts (`960` posts) show slightly higher average likes (`10,208.10`) and engagement rate (`1.038`), and `neutral` posts (`1,527` posts) average the most comments (`1,528.40`).
* **Audience & Device Breakdown:** `mobile` is the most frequent viewing device (`1,684` posts), and `Male` (`1,849`), `Other` (`1,581`), and `Female` (`1,570`) users are fairly evenly distributed across the dataset.

## Business & Policy Recommendations
* **Prioritize Video & High-Engagement Formats:** Expand creator incentives and feed distribution for `video` content, which outperforms other post formats on both average likes and engagement rate.
* **Tailor Regional & Category Strategies:** Pair high-reach markets like `India` with high-engagement markets like `Brazil` and `Australia` by localizing top-volume categories (`fitness`, `tech`, `music`, `education`) for regional audience preferences.
* **Normalize Engagement Rate Reporting:** Use median engagement rates alongside impressions and `engagement_score` (`likes + comments + shares`) in reporting dashboards so small-sample impression spikes do not distort performance rankings.
* **Monitor Controversial & Negative-Sentiment Threads:** Because negative and neutral posts generate strong interaction and comment volume, implement moderation and community-health guardrails that maintain healthy discussion without amplifying harmful or misleading content.
* **Optimize for Mobile & Teen/Young-Adult Safety:** Design media playback and UI experiences around `mobile` consumption while enforcing age-appropriate defaults and well-being prompts for younger users (starting at age 13).

## Tools Used, Tech Stack & Libraries
* **Programming Language:** Python 3
* **Environment:** Jupyter Notebook / Google Colab
* **Core Libraries:** `NumPy`, `Pandas`, `Matplotlib`, `Seaborn`, `Plotly Express`

## Repository Structures
```text
social-media-engagement-analytics/
├── data/
│   └── social_media_engagement_5000.csv
├── notebooks/
│   └── ModEndAssignNmpy.ipynb
├── reports/
│   └── DA V8 M5 - Data Analysis.docx.pdf
└── README.md
```
---
**Author:** Sree Sidhi
