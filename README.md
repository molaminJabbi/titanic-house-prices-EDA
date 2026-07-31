# Titanic Survival Analysis

This repository contains a complete data analysis workflow for the Titanic dataset. It shows how a senior data analyst or data scientist would move from raw data to cleaned data, exploratory analysis, visual insight, and professional reporting.

## Project Overview
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
