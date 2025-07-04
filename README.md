# SISE2601 Project data description
================
Team name
Elias Kanboura & Wasim Khoury & Smeh Diab & Ameer Jamool

This Markdown file describes the data folder structure and organization ...

# README - Sleep Health and Lifestyle Dataset


## Overview

This project aims to classify individuals based on the presence of a sleep disorder (None, Insomnia, or Sleep Apnea) using a variety of health, demographic, and lifestyle features. We apply and compare two machine learning models:

* Multinomial Logistic Regression
* Random Forest Classifier

## Variables

The dataset is the **Sleep Health and Lifestyle Dataset**, which includes 374 observations and 13 variables related to sleep, activity, and physical metrics.
| Variable Name            | Type        | Description                                                   | Example Values                  |
|--------------------------|-------------|---------------------------------------------------------------|---------------------------------|
| Person ID                | Numeric     | A unique ID for each person                                   | 1, 2, 3                         |
| Age                      | Numeric     | Age of the person in years                                    | 25, 37, 60                      |
| Gender                   | Categorical | The biological sex of the person                              | Male, Female                    |
| Occupation               | Categorical | The person’s job or field of work                             | Doctor, Engineer, Teacher       |
| Sleep Duration           | Numeric     | Hours of sleep per night (average)                            | 6.5, 7, 8                       |
| Quality of Sleep         | Numeric     | How good their sleep is (scale 1–10)                          | 6, 7, 9                         |
| Physical Activity Level  | Numeric     | Activity level score (higher means more active)               | 30, 60, 90                      |
| Stress Level             | Numeric     | Self-reported stress level (1–10)                             | 4, 6, 9                         |
| BMI Category             | Categorical | Body Mass Index group                                         | Normal, Overweight, Obese       |
| Blood Pressure           | Categorical | Blood pressure reading                                        | 120/80, 135/85                  |
| Heart Rate               | Numeric     | Resting heart rate (beats per minute)                         | 65, 72, 85                      |
| Daily Steps              | Numeric     | Number of steps the person takes in a day                     | 5000, 8000, 10000               |
| Sleep Disorder           | Categorical | Does the person have a sleep disorder?                        | None, Insomnia, Sleep Apnea     |

## Repository Structure

```
📁 SleepDisorderAnalysis/
├── Final project.Rmd           # The full report written in R Markdown
├── code.Rmd                    # The complete, executable code
└── README.md                   # This file
```

> **Note**: The dataset itself is not included in this repository, as per project submission guidelines.

---

## How to Reproduce the Analysis

To reproduce our analysis end-to-end:

1. **Install R and RStudio**
   Ensure you have the latest version of R and RStudio installed.

2. **Install Required Packages**
   Open RStudio and run:

   ```r
   install.packages(c("tidyverse", "janitor", "skimr", "dplyr", "tidymodels", "nnet", "corrplot", "randomForest"))
   ```

3. **Place the Dataset**
Download the dataset file from Kaggle:

Filename: Sleep_health_and_lifestyle_dataset.csv

Place it in your working directory (the same folder where the .Rmd files are located), or update the file path in the code as needed:

df <- read_csv("Sleep_health_and_lifestyle_dataset.csv")
If you choose a different location, be sure to adjust the file path in the read_csv() function accordingly.

   > You can also update the path in the code (`read_csv(...)`) to match your system.

4. **Run the Analysis**
   Open `code.Rmd` in RStudio and click **"Run All"** or knit it to HTML/PDF to execute the analysis.

---

## Analysis Workflow

The analysis consists of the following steps:

1. **Data Cleaning**

   * Remove irrelevant columns (`person_id`, `occupation`)
   * Split `blood_pressure` into `systolic` and `diastolic`
   * Encode categorical variables (e.g., `gender`, `bmi_category`, `sleep_disorder`)

2. **Exploratory Data Analysis (EDA)**

   * Boxplots, bar plots, scatter plots, correlation matrix
   * Visual exploration of variable relationships to sleep disorders
   
3. **Feature Engineering**

   * Create `bmi_numeric` (ordinal BMI) and `sleep_efficiency` (quality/duration)
   * Normalize numeric features with z-score standardization

4. **Train-Test Split**

   * 80% training, 20% test using stratified sampling by `sleep_disorder`

5. **Modeling and Evaluation**

   * Models: Multinomial Logistic Regression and Random Forest
   * Evaluation: Accuracy, Macro Precision, Macro Recall, Macro F1
   * Check for overfitting by comparing train and test results

6. **Feature Importance Analysis**

   * Extract top predictors using Gini importance from Random Forest
   * Interpret model results in the context of sleep disorder research

---

## Results Summary

* **Top Predictive Features**: Stress Level, Sleep Efficiency, Quality of Sleep
* **Best Performing Model**: Multinomial Logistic Regression slightly outperformed Random Forest in macro metrics
* **No Significant Overfitting** was observed when comparing train and test performance for both models.

---

## Notes

* The dataset is **synthetic** and does not represent real patient data.
* This project was conducted for academic purposes as part of a university course.

---


