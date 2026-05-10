# Online News Popularity -- Probability and Statistics Project

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-green?style=for-the-badge&logo=scikit-learn&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)

**Semester Project | Probability and Statistics (MT-2005) | Spring 2026**  
**FAST NUCES Islamabad**

</div>

---

## Author

| Field | Detail |
|---|---|
| **Name** | Abdul Azeem |
| **Student ID** | 24i-2013 |
| **GitHub** | [@AbdulAzeemHashmi](https://github.com/AbdulAzeemHashmi) |
| **Course** | Probability and Statistics (MT-2005) |
| **Institution** | FAST National University of Computer and Emerging Sciences, Islamabad |

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Repository Structure](#repository-structure)
4. [Project Pipeline](#project-pipeline)
5. [Key Results](#key-results)
6. [Technologies Used](#technologies-used)
7. [How to Run](#how-to-run)
8. [Citation](#citation)

---

## Project Overview

This project analyzes the **UCI Online News Popularity Dataset** to understand what drives social media sharing of online news articles. Two core modeling tasks are performed:

- **Regression:** Predict the number of shares an article will receive using linear regression.
- **Classification:** Classify articles as *High Popularity* (shares >= 1400) or *Low Popularity* (shares < 1400) using logistic regression.

The project also benchmarks the fitted linear regression model against a mean baseline to argue which approach is more suitable for this dataset.

---

## Dataset

| Property | Value |
|---|---|
| **Source** | [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+News+Popularity) |
| **Publisher** | Mashable (www.mashable.com) |
| **Instances** | 39,644 articles |
| **Features** | 61 total (58 predictive, 2 non-predictive, 1 target) |
| **Target Variable** | `shares` (number of times an article was shared) |
| **Classification Threshold** | 1400 shares (Low: 18,490 articles / High: 21,154 articles) |

### Feature Categories

- **Content metrics** -- word count, unique tokens, links, images, videos
- **Keyword statistics** -- min/max/avg shares of best and worst keywords
- **Data channel** -- Lifestyle, Entertainment, Business, Social Media, Tech, World
- **Publication timing** -- day of week, weekend indicator
- **LDA topic scores** -- closeness to 5 latent topics
- **Sentiment and subjectivity** -- polarity, subjectivity, positive/negative word rates
- **Self-reference metrics** -- shares of previously referenced Mashable articles

---

## Repository Structure

```
Probability-and-Statistics-Project/
|
|-- 24i-2013_OnlineNewsPopularity.ipynb   # Main Jupyter notebook (full analysis)
|-- OnlineNewsPopularity.csv              # Dataset (39,644 rows x 61 columns)
|-- OnlineNewsPopularity.names            # Feature descriptions and metadata
|-- README.md                             # Project documentation (this file)
```

---

## Project Pipeline

### 1. Data Preprocessing
- Dropped non-predictive columns (`url`, `timedelta`)
- Removed duplicate rows
- Identified and dropped redundant features (`is_weekend`, `rate_negative_words`)
- Capped extreme outliers in the `shares` column using the IQR method

### 2. Exploratory Data Analysis (EDA)
- Statistical summaries of key features (mean, std, min, max, quartiles)
- Distribution plots for the target variable (raw and log-transformed)
- Article count and average shares by publication day and data channel
- Histograms for 8 key predictor variables
- Scatter plots of selected features against shares (with trend lines)

### 3. Correlation Analysis
- Pearson correlation heatmap covering 15 key features
- Identified top positive and negative correlations with `shares`
- Explained unusual or counterintuitive correlations

### 4. Feature Engineering and Normalization
- Log-transformed the target variable (`log_shares`) to reduce right skew
- Applied `StandardScaler` to all predictor features before modeling
- 80/20 stratified train-test split

### 5. Linear Regression
- Fitted a multivariate linear regression model on log-transformed shares
- Analyzed and visualized regression coefficients by magnitude
- Evaluated using RMSE, MAE, and R-squared

### 6. Regression Assumption Checks
- Residuals vs. Fitted Values plot
- Histogram and Q-Q plot of residuals
- Variance Inflation Factor (VIF) analysis for multicollinearity detection

### 7. Mean Baseline vs. Fitted Model
- Compared linear regression against a naive mean prediction baseline
- Reported percentage improvement in RMSE and MAE
- Argued which model is more suitable with supporting metrics

### 8. Classification
- Classified articles as High (>= 1400 shares) or Low (< 1400 shares)
- Used Logistic Regression as the classifier
- Evaluated using accuracy, precision, recall, F1-score, and confusion matrix
- Also evaluated a threshold-based classifier derived from linear regression predictions

### 9. Hypothesis Testing
Five statistical hypothesis tests were conducted using the Mann-Whitney U test (non-parametric, suitable for non-normal distributions):

| Feature | Null Hypothesis | Result |
|---|---|---|
| `kw_avg_avg` | Keyword avg-shares is equal for both groups | Rejected |
| `num_imgs` | Image count does not differ between groups | Rejected |
| `n_tokens_content` | Article length is equal for both groups | Rejected |
| `global_sentiment_polarity` | Sentiment polarity is equal for both groups | Rejected |
| `self_reference_avg_sharess` | Avg shares of referenced articles is equal | Rejected |

### 10. Significant Predictors Analysis
- Ranked all features by absolute regression coefficient magnitude
- Visualized the top 20 predictors
- Discussed the practical interpretation of each significant feature

---

## Key Results

| Metric | Mean Baseline | Linear Regression |
|---|---|---|
| RMSE | -- | Lower (improved) |
| MAE | -- | Lower (improved) |
| R-squared | 0.0000 | > 0 |

| Model | Task | Accuracy |
|---|---|---|
| Logistic Regression | High/Low Classification | ~60-65% |
| LR Threshold Classifier | High/Low Classification | Comparable |

### Top Predictors of Article Popularity

1. `kw_avg_avg` -- Average shares of best-performing keywords
2. `kw_max_avg` -- Maximum average shares among keywords
3. `self_reference_avg_sharess` -- Historical shares of referenced articles
4. `LDA topic scores` -- Topic relevance signals
5. `data_channel_is_*` -- Content category (Tech and Social Media perform best)

### Notable Insights

- The `shares` distribution is extremely right-skewed. Log-transformation is essential for regression.
- Keyword quality is the single strongest predictor. Articles with share-worthy keywords tend to go viral.
- A rich-get-richer effect exists: articles that cite already-popular content tend to be more popular themselves.
- Raw article length has near-zero correlation with shares. Quality of keywords matters far more than quantity of words.
- Weekend articles receive slightly higher average shares, likely due to reduced publishing competition.
- All 5 hypothesis tests rejected the null hypothesis at alpha = 0.05, confirming that multiple features are statistically associated with popularity.

---

## Technologies Used

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, and manipulation |
| `numpy` | Numerical computations |
| `matplotlib` | Custom static visualizations |
| `seaborn` | Statistical plots including the correlation heatmap |
| `scipy.stats` | Hypothesis testing (Mann-Whitney U) |
| `scikit-learn` | Linear regression, logistic regression, scaling, metrics |
| `statsmodels` | VIF computation and OLS model summary |

---

## How to Run

### Prerequisites

Make sure you have Python 3.10 or later installed.

### Step 1 -- Clone the repository

```bash
git clone https://github.com/AbdulAzeemHashmi/Probability-and-Statistics-Project.git
cd Probability-and-Statistics-Project
```

### Step 2 -- Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn statsmodels jupyter
```

### Step 3 -- Launch the notebook

```bash
jupyter notebook 24i-2013_OnlineNewsPopularity.ipynb
```

### Step 4 -- Run all cells

Go to **Kernel > Restart and Run All** to execute the complete analysis from top to bottom.

> **Note:** Make sure `OnlineNewsPopularity.csv` is in the same directory as the notebook before running.

---

## Citation

If you use this dataset, please cite the original authors:

> K. Fernandes, P. Vinagre and P. Cortez. *A Proactive Intelligent Decision Support System for Predicting the Popularity of Online News.* Proceedings of the 17th EPIA 2015 -- Portuguese Conference on Artificial Intelligence, September, Coimbra, Portugal.

---

<div align="center">
Made with dedication for the Probability and Statistics course at FAST NUCES Islamabad.
</div>
