# Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines

![image](https://github.com/user-attachments/assets/86224035-5ee2-406b-8ff4-8f0204f08a61)

Author: [Tracy Gwehona](tracy.gwehona@gmail.com)

## Overview
In 2009, during the H1N1 influenza outbreak, the U.S. National H1N1 Flu Survey collected extensive data on individuals' vaccination statuses, backgrounds, opinions, and health behaviors. This dataset provides an opportunity to analyze the factors that influenced people's decisions to receive the H1N1 and seasonal flu vaccines.

By predicting vaccination uptake based on these factors, insights can be gained to improve the design and communication strategies for future vaccination campaigns. Public health officials can use these insights to tailor outreach efforts, allocate resources efficiently, and address vaccine hesitancy more effectively.

## Business Understanding
### Stakeholders
Public Health officials.

### Business Problem
The primary goal of this project is to predict whether an individual received the H1N1 flu vaccine based on their demographic information, personal beliefs, and health behaviors. This binary classification task can help public health agencies:

1. Identify patterns among populations who are more or less likely to get vaccinated.
2. Understand barriers to vaccine adoption, such as misconceptions, trust issues, or socio-economic challenges.
3. Develop targeted interventions to increase vaccination rates, especially in communities where uptake is low.
4. Optimize communication strategies by identifying which beliefs and behaviors are most strongly associated with vaccination decisions.

By solving this problem, public health organizations can improve vaccination outreach and preparedness for future epidemics or pandemics, ultimately protecting more people from preventable diseases.

## Data Understanding 
The datasets in use were obtained from [Driven Data](https://www.drivendata.org/competitions/66/flu-shot-learning/). Each row in the datasets represents one person who responded to the National 2009 H1N1 Flu Survey. 

The datasets contain demographic information such as age, health behavior data such as health insurance status and opinions and attitude information such as level of concern about the H1N1 flu, etc.

## Data Cleaning
- I dropped columns with more than 30% of missing values because it would have been difficult to impute meaningful values without introducing bias or noise. Dropping them helps maintain data integrity and simplifies the analysis.
- I then imputed columns with datatype 'float' with their median because median is less affected by extreme values compared to the mean and for numerical data, the median maintains the central tendency without skewing the distribution. Also some of those columns had categorical data just represented by float numbers like 0 and 1.
- I filled the missing values of columns with datatype 'object' with 'unknown' to preserve data integrity and because it is simple and clear; it is an interpretable value that doesn't distort the dataset's meaning.
- I finally converted categorical variables into numerical values by using OneHotEncoder and LabelEncoder.

## Modelling
I used the `Random Forest` classifier.

## Evaluation
The model's performance was evaluated by use of roc-auc score.

**Results**
- **H1N1 Vaccine ROC AUC: 0.8239**: This indicates good predictive performance for the H1N1 vaccine, as values above 0.8 suggest a strong model.
- **Seasonal Vaccine ROC AUC: 0.8475**: This shows even better performance for predicting the seasonal flu vaccine.

✅ **Overall Score: 0.8357**
This is a strong performance, suggesting the model is well-calibrated and performing consistently across both target variables.
