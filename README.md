<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:667eea,100:764ba2&height=200&section=header&text=Online%20News%20Popularity&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Probability%20and%20Statistics%20Project&descAlignY=55&descSize=18" width="100%"/>

<br/>

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-green?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)

<img src="https://img.shields.io/github/stars/AbdulAzeemHashmi/Probability-and-Statistics-Project?style=social" alt="stars"/>
<img src="https://img.shields.io/github/forks/AbdulAzeemHashmi/Probability-and-Statistics-Project?style=social" alt="forks"/>
<img src="https://img.shields.io/github/last-commit/AbdulAzeemHashmi/Probability-and-Statistics-Project?color=blueviolet" alt="last commit"/>

### 🎓 Semester Project | Probability and Statistics (MT 2005) | Spring 2026
### 🏫 FAST NUCES Islamabad

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=764ABA&center=true&vCenter=true&width=650&lines=Predicting+Shares+with+Linear+Regression;Classifying+Popularity+with+Logistic+Regression;Testing+Hypotheses+with+Mann-Whitney+U;Exploring+39%2C644+Mashable+Articles" alt="Typing SVG" />

</div>

<br/>

## 👤 Author

<table>
<tr>
<td>🧑‍💻 <b>Name</b></td>
<td>Abdul Azeem</td>
</tr>
<tr>
<td>🆔 <b>Student ID</b></td>
<td>24i 2013</td>
</tr>
<tr>
<td>🐙 <b>GitHub</b></td>
<td><a href="https://github.com/AbdulAzeemHashmi">@AbdulAzeemHashmi</a></td>
</tr>
<tr>
<td>📘 <b>Course</b></td>
<td>Probability and Statistics (MT 2005)</td>
</tr>
<tr>
<td>🏛️ <b>Institution</b></td>
<td>FAST National University of Computer and Emerging Sciences, Islamabad</td>
</tr>
</table>

<br/>

## 📑 Table of Contents

- [🔍 Project Overview](#-project-overview)
- [📊 Dataset](#-dataset)
- [🗂️ Repository Structure](#️-repository-structure)
- [🚀 Project Pipeline](#-project-pipeline)
- [🏆 Key Results](#-key-results)
- [🛠️ Technologies Used](#️-technologies-used)
- [⚙️ How to Run](#️-how-to-run)
- [📖 Citation](#-citation)

<br/>

## 🔍 Project Overview

This project analyzes the **UCI Online News Popularity Dataset** to understand what drives social media sharing of online news articles. Two core modeling tasks are performed:

- 📈 **Regression:** Predict the number of shares an article will receive using linear regression.
- 🎯 **Classification:** Classify articles as *High Popularity* (shares of 1400 or more) or *Low Popularity* (shares below 1400) using logistic regression.

The project also benchmarks the fitted linear regression model against a mean baseline to argue which approach is more suitable for this dataset.

<div align="center">
<img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" width="400" alt="data analysis animation"/>
</div>

<br/>

## 📊 Dataset

<div align="center">

| Property | Value |
|---|---|
| 🌐 **Source** | [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+News+Popularity) |
| 📰 **Publisher** | Mashable (www.mashable.com) |
| 🔢 **Instances** | 39,644 articles |
| 🧬 **Features** | 61 total (58 predictive, 2 non predictive, 1 target) |
| 🎯 **Target Variable** | `shares` (number of times an article was shared) |
| ⚖️ **Classification Threshold** | 1400 shares (Low: 18,490 articles, High: 21,154 articles) |

</div>

### 🧩 Feature Categories

- 📝 **Content metrics**: word count, unique tokens, links, images, videos
- 🔑 **Keyword statistics**: minimum, maximum and average shares of best and worst keywords
- 📺 **Data channel**: Lifestyle, Entertainment, Business, Social Media, Tech, World
- 🕒 **Publication timing**: day of week, weekend indicator
- 🧠 **LDA topic scores**: closeness to 5 latent topics
- 😊 **Sentiment and subjectivity**: polarity, subjectivity, positive and negative word rates
- 🔁 **Self reference metrics**: shares of previously referenced Mashable articles

<br/>

## 🗂️ Repository Structure

```
Probability-and-Statistics-Project/
├── 📓 24i-2013_OnlineNewsPopularity.ipynb   # Main Jupyter notebook (full analysis)
├── 📄 OnlineNewsPopularity.csv              # Dataset (39,644 rows x 61 columns)
├── 📋 OnlineNewsPopularity.names            # Feature descriptions and metadata
└── 📘 README.md                             # Project documentation (this file)
```

<br/>

## 🚀 Project Pipeline

<details open>
<summary><b>1️⃣ Data Preprocessing</b></summary>
<br/>

- 🗑️ Dropped non predictive columns (`url`, `timedelta`)
- 🧹 Removed duplicate rows
- ✂️ Identified and dropped redundant features (`is_weekend`, `rate_negative_words`)
- 📉 Capped extreme outliers in the `shares` column using the IQR method

</details>

<details>
<summary><b>2️⃣ Exploratory Data Analysis (EDA)</b></summary>
<br/>

- 📊 Statistical summaries of key features (mean, standard deviation, minimum, maximum, quartiles)
- 📈 Distribution plots for the target variable (raw and log transformed)
- 📅 Article count and average shares by publication day and data channel
- 📉 Histograms for 8 key predictor variables
- 🔵 Scatter plots of selected features against shares (with trend lines)

</details>

<details>
<summary><b>3️⃣ Correlation Analysis</b></summary>
<br/>

- 🌡️ Pearson correlation heatmap covering 15 key features
- 🔝 Identified top positive and negative correlations with `shares`
- 💡 Explained unusual or counterintuitive correlations

</details>

<details>
<summary><b>4️⃣ Feature Engineering and Normalization</b></summary>
<br/>

- 🔄 Log transformed the target variable (`log_shares`) to reduce right skew
- ⚖️ Applied `StandardScaler` to all predictor features before modeling
- ✂️ 80/20 stratified train test split

</details>

<details>
<summary><b>5️⃣ Linear Regression</b></summary>
<br/>

- 📐 Fitted a multivariate linear regression model on log transformed shares
- 📊 Analyzed and visualized regression coefficients by magnitude
- ✅ Evaluated using RMSE, MAE and R squared

</details>

<details>
<summary><b>6️⃣ Regression Assumption Checks</b></summary>
<br/>

- 🔍 Residuals vs Fitted Values plot
- 📊 Histogram and Q-Q plot of residuals
- 🧮 Variance Inflation Factor (VIF) analysis for multicollinearity detection

</details>

<details>
<summary><b>7️⃣ Mean Baseline vs Fitted Model</b></summary>
<br/>

- ⚔️ Compared linear regression against a naive mean prediction baseline
- 📈 Reported percentage improvement in RMSE and MAE
- 🏆 Argued which model is more suitable with supporting metrics

</details>

<details>
<summary><b>8️⃣ Classification</b></summary>
<br/>

- 🏷️ Classified articles as High (1400 shares or more) or Low (below 1400 shares)
- 🤖 Used Logistic Regression as the classifier
- ✅ Evaluated using accuracy, precision, recall, F1 score and confusion matrix
- 🔁 Also evaluated a threshold based classifier derived from linear regression predictions

</details>

<details>
<summary><b>9️⃣ Hypothesis Testing</b></summary>
<br/>

Five statistical hypothesis tests were conducted using the Mann-Whitney U test (non parametric, suitable for non normal distributions):

| Feature | Null Hypothesis | Result |
|---|---|---|
| 🔑 `kw_avg_avg` | Keyword average shares is equal for both groups | ❌ Rejected |
| 🖼️ `num_imgs` | Image count does not differ between groups | ❌ Rejected |
| 📝 `n_tokens_content` | Article length is equal for both groups | ❌ Rejected |
| 😊 `global_sentiment_polarity` | Sentiment polarity is equal for both groups | ❌ Rejected |
| 🔁 `self_reference_avg_sharess` | Average shares of referenced articles is equal | ❌ Rejected |

</details>

<details>
<summary><b>🔟 Significant Predictors Analysis</b></summary>
<br/>

- 🏅 Ranked all features by absolute regression coefficient magnitude
- 📊 Visualized the top 20 predictors
- 💬 Discussed the practical interpretation of each significant feature

</details>

<br/>

## 🏆 Key Results

<div align="center">

| Metric | Mean Baseline | Linear Regression |
|---|---|---|
| RMSE | 🔹 baseline | ✅ Lower (improved) |
| MAE | 🔹 baseline | ✅ Lower (improved) |
| R squared | 0.0000 | ✅ Greater than 0 |

| Model | Task | Accuracy |
|---|---|---|
| 🤖 Logistic Regression | High/Low Classification | ⭐ ~60 to 65% |
| 📐 LR Threshold Classifier | High/Low Classification | ⭐ Comparable |

</div>

### 🥇 Top Predictors of Article Popularity

1. 🔑 `kw_avg_avg`: Average shares of best performing keywords
2. 🔑 `kw_max_avg`: Maximum average shares among keywords
3. 🔁 `self_reference_avg_sharess`: Historical shares of referenced articles
4. 🧠 LDA topic scores: Topic relevance signals
5. 📺 `data_channel_is_*`: Content category (Tech and Social Media perform best)

### 💡 Notable Insights

- 📉 The `shares` distribution is extremely right skewed. Log transformation is essential for regression.
- 🔑 Keyword quality is the single strongest predictor. Articles with share worthy keywords tend to go viral.
- 🔁 A rich get richer effect exists: articles that cite already popular content tend to be more popular themselves.
- 📝 Raw article length has near zero correlation with shares. Quality of keywords matters far more than quantity of words.
- 📅 Weekend articles receive slightly higher average shares, likely due to reduced publishing competition.
- ✅ All 5 hypothesis tests rejected the null hypothesis at alpha equal to 0.05, confirming that multiple features are statistically associated with popularity.

<br/>

## 🛠️ Technologies Used

<div align="center">

| Library | Purpose | Icon |
|---|---|---|
| `pandas` | Data loading, cleaning and manipulation | 🐼 |
| `numpy` | Numerical computations | 🔢 |
| `matplotlib` | Custom static visualizations | 📊 |
| `seaborn` | Statistical plots including the correlation heatmap | 🌊 |
| `scipy.stats` | Hypothesis testing (Mann-Whitney U) | 🧪 |
| `scikit-learn` | Linear regression, logistic regression, scaling, metrics | 🤖 |
| `statsmodels` | VIF computation and OLS model summary | 📐 |

<br/>

![Python](https://skillicons.dev/icons?i=python)
&nbsp;
![Jupyter](https://skillicons.dev/icons?i=jupyter)
&nbsp;
![Sklearn](https://skillicons.dev/icons?i=sklearn)

</div>

<br/>

## ⚙️ How to Run

### ✅ Prerequisites

Make sure you have Python 3.10 or later installed.

### 1️⃣ Clone the repository

```bash
git clone https://github.com/AbdulAzeemHashmi/Probability-and-Statistics-Project.git
cd Probability-and-Statistics-Project
```

### 2️⃣ Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn statsmodels jupyter
```

### 3️⃣ Launch the notebook

```bash
jupyter notebook 24i-2013_OnlineNewsPopularity.ipynb
```

### 4️⃣ Run all cells

Go to **Kernel > Restart and Run All** to execute the complete analysis from top to bottom.

> ⚠️ **Note:** Make sure `OnlineNewsPopularity.csv` is in the same directory as the notebook before running.

<br/>

## 📖 Citation

If you use this dataset, please cite the original authors:

> K. Fernandes, P. Vinagre and P. Cortez. *A Proactive Intelligent Decision Support System for Predicting the Popularity of Online News.* Proceedings of the 17th EPIA 2015, Portuguese Conference on Artificial Intelligence, September, Coimbra, Portugal.

<br/>

<div align="center">

### ⭐ If you found this project helpful, consider giving it a star

<a href="https://github.com/AbdulAzeemHashmi/Probability-and-Statistics-Project/stargazers">
<img src="https://img.shields.io/badge/Star%20this%20repo-⭐-yellow?style=for-the-badge" alt="star this repo"/>
</a>

<br/><br/>

Made with 💜 and dedication for the Probability and Statistics course at FAST NUCES Islamabad.

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:764ba2,100:667eea&height=100&section=footer" width="100%"/>

</div>
