# Titanic Survival Analysis

This repository contains a complete data analysis workflow for the Titanic dataset. It shows how a senior data analyst or data scientist would move from raw data to cleaned data, exploratory analysis, visual insight, and professional reporting.

## Project Overview\
The goal of this project is to understand which factors influenced passenger survival on the Titanic. The analysis explores how variables such as gender, passenger class, age, fare, and embarkation port relate to the outcome.

## What this project includes
- A full analysis notebook: [week1_2/titanic.ipynb](week1_2/titanic.ipynb)
- A detailed written report: [week1_2/Titanic_Analysis_Report.md](week1_2/Titanic_Analysis_Report.md)
- Visual outputs saved in [week1_2/Assets/images](week1_2/Assets/images)

## Project Structure
- [week1_2/titanic.ipynb](week1_2/titanic.ipynb) - main analysis notebook
- [week1_2/data/Titanic-Dataset.csv](week1_2/data/Titanic-Dataset.csv) - raw dataset
- [week1_2/data/titanic_cleaned.csv](week1_2/data/titanic_cleaned.csv) - cleaned dataset
- [week1_2/Assets/images](week1_2/Assets/images) - charts and plots

## Analysis Workflow
1. Data import and inspection
2. Data cleaning and validation
3. Feature engineering
4. Exploratory data analysis
5. Insight interpretation and reporting

## Key Findings
- The overall survival rate was lower than the death rate.
- Female passengers had a much higher survival rate than male passengers.
- First-class passengers had a significantly higher survival rate than third-class passengers.
- Higher fares were associated with better survival outcomes.
- Children showed a more favorable survival pattern than many other age groups.

## Visual Summary
The charts below make the main findings easier to understand at a glance.

![Overall Survival]([week1_2/Assets/images/survival_](https://github.com/molaminJabbi/titanic-house-prices-EDA/blob/main/Assets/images/Survival_rate_by_Pclass.png)rate.png)

![Survival by Gender](week1_2/Assets/images/titanic_survival_by_gender.png)

![Survival by Passenger Class](week1_2/Assets/images/Survival_rate_by_Pclass.png)

![Survival by Age Group](week1_2/Assets/images/AgeGroup_survival_rate.png)

![Embarkation Port Distribution](week1_2/Assets/images/Embarked.png)

![Correlation Matrix](week1_2/Assets/images/correlation_matrix.png)

## Tools Used
- Python
- pandas
- NumPy
- Matplotlib
- Seaborn

## How to Run
1. Open [week1_2/titanic.ipynb](week1_2/titanic.ipynb) in Jupyter Notebook or VS Code.
2. Install the required libraries if needed.
3. Run the cells in order to reproduce the analysis.

## Next Steps
- Build a predictive model to estimate passenger survival.
- Compare several machine learning algorithms.
- Turn the analysis into a dashboard or interactive report.

## License
This project is intended for educational and portfolio purposes.


# DATA CLEANING & EXPLORATORY DATA ANALYSIS
# TITANIC - EDA
## Problem Statement\
In the 90s, the titanic sank after colliding with an iceberg, resulting in the deaths of over 1,500 of the approximately 2,224 passengers and crew aboard. Survival was not random — evacuation protocol, ticket class, and passenger demographics all played a role in who made it off the ship alive.

**This analysis investigates:** which passenger characteristics were most associated with survival, and what does that reveal about how the evacuation actually played out? Understanding this is a template for a broader class of problems — identifying which factors predict an outcome in an imbalanced, real-world dataset — before any predictive model is built.

## Dataset:\
[Original titanic dataset](https://www.kaggle.com/datasets/yasserh/titanic-dataset)\
[Cleaned titanic dataset](data/titanic_cleaned.csv)\
Size: 891 records, 12 columns\
Target Variable: Survived (0= not survived, 1= Survived)

## Methodology\
1. Data Cleaning\
Checked for missing values and duplicates. Found no duplicate rows.
Missing values identified: Age (177 of 891 records, ~20%), Cabin (687 of 891, ~77%), Embarked (2 of 891).
Dropped Cabin — too sparse (77% missing) to reliably impute or use.
Imputed missing Age values with the column median.
Imputed the 2 missing Embarked values with 'S' (Southampton), based on the fact that Southampton was overwhelmingly the most common port of embarkation for 1st-class passengers (the class both missing records belonged to).

3. Handling Data Irregularities\
Found 15 records with a Fare of 0, which is not realistic for a paying passenger.
Corrected these by replacing 0 with the median fare for that passenger's Pclass, rather than a single global median — since fare is strongly tied to class.

3. Feature Engineering\
Created an AgeGroup categorical feature (Child, Teenager, Young Adult, Middle-aged, Senior) by binning Age, to support more interpretable group-level comparisons than raw age values.

4. Exploratory Analysis\
Univariate analysis of survival rate, port of embarkation, age, and fare distributions.
Bivariate analysis of survival against gender, passenger class, and age group.
Correlation analysis across all numeric features against the survival outcome.

### Visual Summary\
[Survival rate](Assets/images/survival_rate.png)\
[Survival by passenger class](Assets/images/Survival_rate_by_Pclass.png)\
[Survival by Gender](Assets/images/titanic_survival_by_gender.png)

Limitations\

Median imputation for Age creates an artificial spike at the median value (visible in the age distribution), which slightly understates the true variance in passenger age.
Cabin was dropped rather than used to derive deck-level features (e.g., proximity to lifeboats), which could have added predictive signal at the cost of working with a sparse column.
This is a well-known, heavily studied dataset — many of the patterns found here (class and gender effects) are consistent with historical accounts of the evacuation, which increases confidence in the analysis but also means the findings are more confirmatory than novel.

What's Next\
Full findings are documented in insight_summary.md\
Week 3: statistical hypothesis testing on the relationships identified here (e.g., is the survival gap between classes statistically significant?).\
Week 4: build a Logistic Regression model to predict survival, evaluated with Accuracy.

Tech Stack\
Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

