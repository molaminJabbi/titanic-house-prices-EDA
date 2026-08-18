# Titanic Survival Analysis - EDA

## Problem Statement

In 1912, the Titanic sank after colliding with an iceberg, resulting in the deaths of over 1,500 of the approximately 2,224 passengers and crew aboard. Survival was not random — evacuation procedures, passenger characteristics, and crew decisions significantly influenced who lived and who perished.

## Project Overview

The goal of this project is to understand which factors influenced passenger survival on the Titanic. The analysis explores how variables such as gender, passenger class, age, fare, and embarkation port determined survival outcomes during this historical disaster.

**This analysis investigates:** Which passenger characteristics were most associated with survival, and what does that reveal about how the evacuation actually played out? Understanding this is valuable for historical context and demonstrates how systematic biases (e.g., "women and children first") manifested in real-world crisis scenarios.

---

## Dataset

| Item | Details |
|------|---------|
| **Original Dataset** | [Titanic Dataset on Kaggle](https://www.kaggle.com/datasets/yasserh/titanic-dataset) |
| **Cleaned Dataset** | `data/titanic_cleaned.csv` |
| **Size** | 891 records, 12 features |
| **Target Variable** | `Survived` (0 = did not survive, 1 = survived) |

## Methodology

### 1. Data Cleaning

- **Duplicates:** Checked for duplicate rows — none found.
- **Missing Values Identified:**
  - `Age`: 177 of 891 records (~20% missing)
  - `Cabin`: 687 of 891 records (~77% missing)
  - `Embarked`: 2 of 891 records (~0.2% missing)

- **Handling Missing Values:**
  - **Cabin (dropped):** Too sparse (77% missing) to reliably impute or derive meaningful features. Dropping was more prudent than attempting deck-level feature engineering.
  - **Age (imputed with median):** Filled with 28.0 (column median). Median chosen to minimize bias from age distribution skewness.
  - **Embarked (imputed with 'S'):** Both missing values occurred in 1st-class passengers. Southampton ('S') was the most common port for 1st-class embarkation (72.4% of 1st-class passengers), making it the most statistically justified imputation.

### 2. Handling Data Irregularities

- **Fare = 0 Issue:** Found 15 records with a Fare of 0, which is unrealistic for paying passengers.
- **Resolution:** Replaced 0 values with the median fare for that passenger's `Pclass`, rather than a single global median. This approach respects the strong relationship between ticket price and passenger class.

### 3. Feature Engineering

- **AgeGroup:** Created a categorical feature by binning `Age` into five groups:
  - Child (0-12)
  - Teenager (13-19)
  - Young Adult (20-35)
  - Middle-aged (36-60)
  - Senior (61+)
  - This binning supports more interpretable group-level comparisons than raw age values and reduces model complexity.

### 4. Exploratory Analysis

- **Univariate Analysis:** Examined distributions of survival rate, port of embarkation, age, and fare.
- **Bivariate Analysis:** Analyzed survival rates across gender, passenger class, and age group.
- **Correlation Analysis:** Computed Pearson correlations between numeric features and the survival outcome.

---

## Key Findings

### Survival Overview

**Overall Survival Rate:** 38.4% (342 of 891 passengers survived)

![Survival Rate Distribution](Assets/images/survival_rate.png)

---

### By Passenger Class

**Key Insight:** 1st-class passengers were **2.6× more likely** to survive than 3rd-class passengers, reflecting priorities in evacuation procedures and lifeboat access.

| Class | Survival Rate | Count |
|-------|---------------|-------|
| 1st Class | 62.9% | 136/217 |
| 2nd Class | 47.3% | 87/184 |
| 3rd Class | 24.2% | 119/490 |

![Survival by Passenger Class](Assets/images/Survival_rate_by_Pclass.png)

---

### By Gender

**Key Insight:** The **"women and children first" protocol** was clearly enforced; females were **3.9× more likely** to survive than males.

| Gender | Survival Rate | Count |
|--------|---------------|-------|
| Female | 74.2% | 233/314 |
| Male | 18.9% | 109/577 |

![Survival by Gender](Assets/images/titanic_survival_by_gender.png)

---

### By Age Group

**Key Insight:** Age mattered significantly, with children prioritized and elderly passengers less likely to survive.

- **Children (0-12):** ~67% survival rate
- **Teenagers (13-19):** ~45% survival rate
- **Young Adults (20-35):** ~36% survival rate
- **Middle-aged (36-60):** ~40% survival rate
- **Seniors (61+):** ~27% survival rate

![Survival by Age Group](Assets/images/AgeGroup_survival_rate.png)

---

### Port of Embarkation

![Embarkation Port Distribution](Assets/images/Embarked.png)

---

### Top Correlations with Survival

| Feature | Correlation | Interpretation |
|---------|-------------|-----------------|
| Pclass | -0.34 | Higher class (lower number) → higher survival |
| Sex (encoded: male=0, female=1) | +0.54 | Being female strongly increases survival odds |
| Fare | +0.25 | Higher fare → better survival chances |
| Age | -0.06 | Weak negative correlation; younger slightly favored |
| SibSp | -0.04 | Weak negative; family relations slightly decrease odds |
| Parch | +0.08 | Weak positive; having parents/children slightly increases odds |

![Feature Correlation Matrix](Assets/images/correlation_matrix.png)

**Key Finding:** Class and gender were the strongest predictors of survival, followed by fare (which correlates with class). Family size and age had minimal impact on survival odds.

---

## Limitations

1. **Median Imputation Artifacts:** Imputing Age with the median (28.0 years) creates an artificial spike in the age distribution, slightly understating true age variance. This could bias downstream models; alternative methods (KNN, MICE) could be explored.

2. **Cabin Data Loss:** Cabin was dropped entirely rather than used to derive deck-level features (e.g., proximity to lifeboats), which could have added predictive signal. The 77% sparsity made this trade-off necessary.

3. **Small Sample for Embarked:** Only 2 records had missing embarkation; while the imputation is justified, the sample size is too small to validate statistically.

4. **Dataset Limitations:** This is a well-known, heavily studied dataset. Many patterns found here (class and gender effects) are consistent with historical accounts, increasing confidence in results but reducing novelty. Future work should focus on predictive modeling rather than descriptive analysis.

---

## Next Steps

- **Phase 2:** Conduct statistical hypothesis testing on relationships identified (e.g., chi-squared tests for independence between class and survival).
- **Phase 3:** Build predictive models (Logistic Regression, Random Forest) using the cleaned dataset; evaluate with Accuracy, Precision, Recall, and AUC-ROC.
- **Phase 4:** Perform feature importance analysis to quantify the relative impact of each variable on model predictions.

---

## Tech Stack

|Python| |Pandas| |NumPy| |Matplotlib| |Seaborn| |Jupyter Notebook|

---
