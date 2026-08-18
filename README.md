# DATA CLEANING & EXPLORATORY DATA ANALYSIS
# TITANIC - EDA
## Problem Statement
In the 90s, the titanic sank after colliding with an iceberg, resulting in the deaths of over 1,500 of the approximately 2,224 passengers and crew aboard. Survival was not random — evacuation protocol, ticket class, and passenger demographics all played a role in who made it off the ship alive.

## Project Overview
The goal of this project is to understand which factors influenced passenger survival on the Titanic. The analysis explores how variables such as gender, passenger class, age, fare, and embarkation port relate to the outcome.

**This analysis investigates:** which passenger characteristics were most associated with survival, and what does that reveal about how the evacuation actually played out? Understanding this is a template for a broader class of problems — identifying which factors predict an outcome in an imbalanced, real-world dataset — before any predictive model is built.

## Dataset:
[Original titanic dataset](https://www.kaggle.com/datasets/yasserh/titanic-dataset)\
[Cleaned titanic dataset](data/titanic_cleaned.csv)\
Size: 891 records, 12 columns\
Target Variable: Survived (0= not survived, 1= Survived)

## Methodology
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

### Visual Summary
[Survival rate](Assets/images/survival_rate.png)\
[Survival by passenger class](Assets/images/Survival_rate_by_Pclass.png)\
[Survival by Gender](Assets/images/titanic_survival_by_gender.png)\
[Embarked](Aseets\images/Embarked.png)\
[Correlation matrix](Assets\images/corrlation_matrix.png)\
[Survival By Age Group](Assets\images/AgeGroup_survival_rate.png)\
## Limitations

Median imputation for Age creates an artificial spike at the median value (visible in the age distribution), which slightly understates the true variance in passenger age.
Cabin was dropped rather than used to derive deck-level features (e.g., proximity to lifeboats), which could have added predictive signal at the cost of working with a sparse column.
This is a well-known, heavily studied dataset — many of the patterns found here (class and gender effects) are consistent with historical accounts of the evacuation, which increases confidence in the analysis but also means the findings are more confirmatory than novel.

What's Next\
Full findings are documented in insight_summary
Week 3: statistical hypothesis testing on the relationships identified here (e.g., is the survival gap between classes statistically significant?).\
Week 4: build a predictive model to predict survival, evaluated with Accuracy.

Tech Stack\
Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

