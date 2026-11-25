#### 💧 Water Potability Analysis & Classification (R)

An end-to-end exploratory data analysis, statistical hypothesis testing, and machine learning classification project evaluating **3,276 water quality records** across nine physicochemical parameters to predict drinking water safety (Potable = 1 vs. Not Potable = 0). 

#### 📄 Project Deliverables

* **[Executive Summary (PDF)](./Executive-Summary.pdf)** — A concise 3-page visual brief highlighting key insights, model performance, and public health recommendations.
* **[Full Technical Report (PDF)](./Water-Potability-Project.pdf)** — Complete R Markdown report including code, statistical diagnostics, visualizations, and model tuning.
* **[Source Code (.Rmd)](./Water-Potability-Project.Rmd)** — Reproducible R Markdown analysis built with tidyverse and tidymodels.


#### 🔍 Key Findings & Methodology

* **Missing Data Diagnostics:** Confirmed that missing values in Sulfate (23.8%), ph (15.0%), and Trihalomethanes (4.9%) were Missing Completely at Random (MCAR 𝑝-value = 0.890⁠) and applied median imputation after verifying all values fell within physically realistic water ranges.
* **Statistical Testing:** Predictors showed no multicollinearity (|𝑟| ≤ 0.15⁠), violated strict normality (Shapiro-Wilk 𝑝-value < 0.05)⁠ for 7 of 9 variables), and showed no single-variable median differences (Mann-Whitney 𝑝-value > 0.05⁠). However, Levene’s test revealed significant variance differences across potability groups for Sulfate, Hardness, Chloramines, ph, and Solids (𝑝-value < 0.05⁠), demonstrating that potability relies on multi-variable, non-linear interactions.
* **Model Comparison (tidymodels):** Evaluated tuned **Random Forest** and **XGBoost** classifiers using an 80/20 stratified train-test split and 5-fold cross-validation. **Random Forest** outperformed XGBoost on unseen test data (**ROC-AUC = 0.689** vs. 0.656; **Accuracy = 67.4%** vs. 65.4%), beating the 61.0% majority-class baseline.
* **Top Predictors & Risk Trade-off:** ph, Sulfate, Hardness, Solids, and Chloramines emerged as the strongest drivers. The model catches **85.5%** of unsafe water samples (342 / 400), making it well suited as a conservative pre-screening filter paired with confirmatory laboratory testing.

#### 🛠️ Tools & Packages Used

* **Language:** R / R Markdown
* **Data Wrangling & Visualization:** tidyverse (dplyr, tidyr, ggplot2), knitr
* **Statistical Diagnostics:** naniar, car, e1071, corrplot
* **Machine Learning:** tidymodels, ranger (Random Forest), xgboost

#### 📊 Data Source

Public dataset from Kaggle: [Water Quality / Potability Dataset](https://www.kaggle.com/datasets/adityakadiwal/water-potability) (CC0: Public Domain).
