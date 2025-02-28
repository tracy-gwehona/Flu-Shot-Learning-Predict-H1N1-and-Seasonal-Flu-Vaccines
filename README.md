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
I utilized a couple of models:
1. **Random Forest Classifier**.
2. **XGBoost Classifier**.
3. **CatBoost Classifier**.
4. **Voting Classifier**

## Evaluation
The model's performance was evaluated by use of roc-auc score.

### Results
#### 1. Random Forest Classifier
- **H1N1 Vaccine ROC AUC: 0.8239**: This indicates good predictive performance for the H1N1 vaccine, as values above 0.8 suggest a strong model.
- **Seasonal Vaccine ROC AUC: 0.8475**: This shows even better performance for predicting the seasonal flu vaccine.

✅ **Overall Score: 0.8357**: This is a strong performance, suggesting the model is well-calibrated and performing consistently across both target variables.

**`Tuning the parameters`**,

- **H1N1 Vaccine ROC AUC: 0.8299**: This shows a slight improvement in predictive performance for the H1N1 vaccine, demonstrating that the optimization has helped the model to make more accurate predictions compared to the non-optimized version (0.8239).
- **Seasonal Vaccine ROC AUC: 0.8515**: Similarly, the seasonal flu vaccine prediction has improved slightly, with the optimized model performing better than the non-optimized version (0.8475).

✅ **Overall Score: 0.8407**: The overall performance improves from 0.8357 to 0.8407, indicating a more robust model after optimization.

The optimized Random Forest model provides a slight boost in ROC AUC scores for both target variables (H1N1 and Seasonal vaccines), improving by 0.0060 and 0.0040, respectively.
The overall ROC AUC score increases by 0.0050, showing a slight but noticeable improvement in model performance.

**Conclusion**: 

While the improvements are modest, the optimized Random Forest model outperforms the non-optimized version, making it the more reliable model in terms of predictive accuracy for both target variables.


#### 2. XGBoost Classifier
- **H1N1 Vaccine ROC AUC: 0.8124**: This indicates decent predictive performance for the H1N1 vaccine. While values above 0.8 suggest a strong model, this score is slightly lower than the optimized Random Forest model, which had a higher AUC of 0.82998, demonstrating that the Random Forest model performed a bit better in predicting the H1N1 vaccine.
- **Seasonal Vaccine ROC AUC: 0.8450**: This shows a comparable performance for predicting the seasonal flu vaccine, with the XGBoost model showing an AUC close to that of the optimized Random Forest model (0.85148). Though the scores are nearly identical, the Random Forest model still slightly outperforms the XGBoost model here.

✅ **Overall Score: 0.8287**: While the XGBoost model performs well, the overall score is slightly lower than the optimized Random Forest model's 0.84073. This suggests that the Random Forest model has more consistent performance across both target variables, whereas the XGBoost model is performing slightly weaker in comparison.

**Conclusion**:

The **optimized Random Forest model** outperforms the **non-optimized XGBoost model** in both target variables (H1N1 and Seasonal vaccine) and the overall ROC AUC score. This suggests that, in this case, the Random Forest model is better at making accurate predictions than the non-optimized XGBoost model. 

However, further optimization of the XGBoost model could potentially improve its performance and allow it to compete more closely with the Random Forest model.

**`Tuning the parameters`**,

- **H1N1 Vaccine ROC AUC: 0.8344**: This shows a solid performance for predicting the H1N1 vaccine, with a slight improvement over the non-optimized XGBoost score of 0.81237.
- **Seasonal Vaccine ROC AUC: 0.8582**: The performance for predicting the seasonal flu vaccine is significantly better, surpassing both the non-optimized XGBoost score (0.84504) and optimized Random Forest (0.85148).

✅ **Overall ROC AUC Score: 0.8463**: This score is an improvement over both the non-optimized XGBoost (0.8287) and optimized Random Forest (0.84073). It indicates that Optimized XGBoost is performing better overall.

**Conclusion**:

**Optimized XGBoost** appears to outperform **Optimized Random Forest** overall. It has stronger predictive power, especially for the _Seasonal vaccine_, but the _H1N1 vaccine_ performance is quite similar across both models.

#### 3. CatBoost Classifier
- **H1N1 Vaccine ROC AUC Score: 0.8279**: The CatBoost model shows solid performance for predicting the H1N1 vaccine, though it is slightly lower than the optimized XGBoost score of 0.8344. This indicates that the CatBoost model could benefit from further tuning to match XGBoost's performance in this area.
- **Seasonal Vaccine ROC AUC Score: 0.8579**: The CatBoost model performs very well in predicting the seasonal vaccine, with a score of 0.8579, which is very close to the optimized XGBoost score of 0.8582. This indicates that the CatBoost model is highly effective at this task, showing minimal performance difference compared to XGBoost.

✅ **Overall ROC AUC Score: 0.8429**: Performance is slightly lower than XGBoost's 0.8463. While there is a small performance gap, CatBoost still provides strong predictive power, especially in handling categorical features and dataset characteristics that may benefit from its tree-based structure.

**Conclusion**:

CatBoost shows **strong performance overall**, with minimal difference from Optimized XGBoost. Fine-tuning the hyperparameters could further improve its performance, especially for tasks like predicting the H1N1 vaccine.

**`Tuning the parameters`**,

- **H1N1 Vaccine ROC AUC: 0.8351**: Slightly outperforms Optimized XGBoost (0.8344), showing a marginal improvement in predicting H1N1 vaccination.
- **Seasonal Vaccine ROC AUC: 0.8570**: Performs slightly lower than Optimized XGBoost (0.8582), but still highly competitive.

✅ **Overall ROC AUC Score: 0.8461**: Almost identical to Optimized XGBoost (0.8463), indicating both models are performing at a similar level.

**Conclusion**:

Optimized CatBoost and XGBoost are closely matched, with CatBoost performing slightly better for H1N1 but XGBoost excelling for Seasonal vaccine. Both models are strong choices, with minimal differences in overall performance. 

**NOTE**:

To leverage the strengths of each model and further improve predictive performance, I will apply an ensemble method using a Voting Classifier. This ensemble method will combine the predictions of the three models—Optimized Random Forest, Optimized XGBoost, and Optimized CatBoost—allowing us to make the final prediction based on the majority vote. By using this approach, we aim to enhance accuracy, reduce overfitting, and create a more robust model that benefits from the diverse strengths of each individual algorithm.

#### 4. Voting Classifier
The Voting Classifier has shown a slight improvement in performance over the individual models:
- **H1N1 Vaccine ROC AUC: 0.83585**: This is a small but noticeable improvement over the Optimized XGBoost score of 0.83440 and CatBoost score of 0.82793 for H1N1 prediction, indicating better model performance due to the ensemble approach.
- **Seasonal Vaccine ROC AUC: 0.85785**: The Voting Classifier also performs better for the Seasonal vaccine, with a slight boost compared to Optimized XGBoost's 0.85823, showing that combining the models helps to balance out their strengths.

✅ **Overall ROC AUC Score: 0.84685**: The Voting Classifier achieves a marginal improvement over both Optimized XGBoost (0.84632) and CatBoost (0.84294), demonstrating that combining the models has led to better overall performance.

**Conclusion**: 

The **Voting Classifier** effectively combines the strengths of **Optimized Random Forest**, **Optimized XGBoost**, and **Optimized CatBoost**, leading to an overall improved performance in predicting both H1N1 and Seasonal vaccines. 

This ensemble method enhances predictive power, making it a solid choice for the **final model**.
