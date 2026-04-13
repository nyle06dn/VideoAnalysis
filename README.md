# YouTube Video Data Analysis

A comprehensive data cleaning and exploratory analysis workflow for YouTube trending video data.

<img width="1185" height="415" alt="image" src="https://github.com/user-attachments/assets/efe7393f-cfed-4d2a-9f7d-ce33afba75f1" />


## Overview

This project analyzes trending YouTube video datasets from the **United States (US)** and **Great Britain (GB)**, covering data loading, cleaning, feature engineering, exploratory analysis, and country-specific insights.

---

## Dataset

| File | Description |
|------|-------------|
| `USvideos.csv` | Trending YouTube videos from the United States |
| `GBvideos.csv` | Trending YouTube videos from Great Britain |

**Key columns:** `video_id`, `title`, `channel_title`, `category_id`, `tags`, `views`, `likes`, `dislikes`, `comment_total`, `thumbnail_link`, `date`

---

## Project Structure

```
├── VideoAnalysis-HW.ipynb        # Main analysis notebook
├── USvideos.csv                  # US trending video data
├── GBvideos.csv                  # GB trending video data
├── cleaned_youtube_trending_data.csv  # Output: cleaned dataset
├── top_categories.png            # Output: top categories visualization
└── README.md
```

---

## Workflow

### Step 1 — Environment Setup
Imports required libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy`, and `glob`.

### Step 2 — Data Loading
Loads all CSV files using `glob`, extracts country codes from filenames, and tags each row with its country of origin.

### Step 3 — Data Cleaning
Converts key string columns (`video_id`, `title`, `channel_title`, `category_id`, `tags`, `thumbnail_link`) to the `string` dtype for consistency.

### Step 4 — Missing Value Analysis
Computes missing value counts and percentages per country:

| Country | Missing Count | Missing % |
|---------|--------------|-----------|
| US      | 7,998        | 8.33%     |
| GB      | 33           | 0.03%     |

### Step 5 — Data Integration
Combines all country DataFrames into a single unified dataset (~15,985 rows), removes duplicates, and prepares the data for analysis.

### Step 6 — Feature Engineering
Creates the following derived features:

| Feature | Description |
|---------|-------------|
| `like_ratio` | `likes / dislikes` |
| `engagement_rate` | `(likes + dislikes + comment_total) / views` |
| `title_length` | Character count of video title |
| `title_word_count` | Word count of video title |
| `title_has_exclamation` | Binary flag — title contains `!` |
| `tags_count` | Number of pipe-separated tags |

### Step 7 — Exploratory Data Analysis
- **Views vs. Likes scatter plot** — 1,000-row sample, color-coded by country (US = blue, GB = red)
- **Engagement Rate boxplot** — Comparison across countries

### Step 8 — Country-Specific Analysis
For each country (US and GB):
- Views distribution histogram (log scale)
- Dislikes distribution histogram

### Step 9 — Advanced Insights
Custom analysis exploring whether videos with more views tend to have more dislikes.

### Step 10 — Saving Results
- Cleaned data exported to `cleaned_youtube_trending_data.csv`
- Top categories visualization saved to `top_categories.png`

---

## Requirements

```
numpy
pandas
matplotlib
seaborn
scipy
```

Install with:
```bash
pip install numpy pandas matplotlib seaborn scipy
```

---

## Usage

1. Place `USvideos.csv` and `GBvideos.csv` in the same directory as the notebook.
2. Open `VideoAnalysis-HW.ipynb` in Jupyter Lab or Jupyter Notebook.
3. Run all cells sequentially.
4. Cleaned output and visualizations will be saved automatically.

---

## Key Findings

- The combined dataset contains **~15,985 records** across US and GB.
- US data has significantly more missing values (~8.33%) compared to GB (~0.03%).
- Average video title length is ~48 characters with ~18 tags per video.
- Median views sit around **312K**, with a maximum of ~59M.
