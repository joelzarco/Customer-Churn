# **Customer-Churn**

This project aimed to develop a model capable of predicting customer churn for a telecommunications company. The project followed a plan consisting of data exploration, preprocessing, feature engineering, model training, and evaluation. Here's my final assessment addressing the key questions:

**1. Steps Completed and Omitted:**

Completed Steps:

* Data loading and initial exploration for contract, personal, internet, and phone datasets.
* Data preprocessing: Handling missing values, encoding categorical features, transforming columns from Yes/No to Boolean values, feature creation (ContractDuration in days).
* Merging datasets into a comprehensive dataset (telecom).
* Addressing class imbalance using RandomOverSampler after one failed test with undersampling.
* Training a LightGBM classifier with standard scaling.
* Hyperparameter optimization using Optuna.
* Model evaluation using AUC-ROC and accuracy.
* Omitted Steps (and why):

Feature engineering (Family, DigitalServices) were attempted but did not significantly improve model performance. They were omitted after testing to prevent overfitting and unnecessary complexity.
Undersampling was initially tried but was replaced by oversampling as it showed better results.

**2. Difficulties Encountered and Resolutions:**

Target variable Type: At the begining of the project it was not clear to me why did the target variable EndDate had incompatible values like 'No' and 'dates' at the same time, but after some analysis it became clear the necessity to refactor it in a new variable Churn.
Class Imbalance: The target variable (Churn) showed a moderate class imbalance, which could bias model predictions towards the majority class. To address this, I used RandomOverSampler to generate synthetic samples, ensuring balanced class distribution in the training data.
Model Performance: Initial models (Random Forest with default parameters, LightGBM with default parameters) did not achieve the desired AUC-ROC score of 0.88 but gave a solid baseline to improve latter on. To achieve this, I optimized hyperparameters using Optuna, resulting in a significant improvement in the model's performance.
Feature Engineering: Initially, features like Family and DigitalServices were created, hoping to improve model performance, but their contributions were close to zero, and they were ultimately removed. This demonstrates the need for careful feature selection and evaluation.
Dataset Merging: There were slight challenges in merging the dataframes (especially internet and phone), as not every contract had internet or phone service. Carefully handling missing values was crucial to prevent issues during model training.
**3. Key Steps in Solving the Task:**

Addressing Class Imbalance: Using RandomOverSampler was a critical step to reduce bias during model training.
Hyperparameter Tuning: Optuna significantly enhanced model performance by optimizing the LightGBM model's parameters after a small number of trials. Randomized Search with cross validation was not used due to previous experiencies that resulted in a huge ammount of compute power.
Feature Engineering: Although not all features were successful, the process of creating features like ContractDuration helped improve the model's understanding of the data.
Model Selection: Choosing a robust model like LightGBM and comparing it with a baseline model allowed for identifying opportunities for improvements and understanding the effectiveness of different techniques. XGBoost was not tested due to its incompatibility with hyperparameter tunning methods found in previuos sprints.
**4. Final Model and Quality Level:**

Final Model: The final model is a LightGBM classifier with hyperparameters optimized using Optuna.
Quality Level: The model achieves an AUC-ROC score of over 0.9052, which significantly surpasses the project's minimum requirement of 0.88. This indicates a high level of accuracy and effectiveness in predicting customer churn.
Conclusion:

**This project successfully built a model capable of accurately predicting customer churn, which can help the company proactively manage customer retention strategies. The lessons learned from this project will be valuable in future machine learning endevours which has been my favorite area of study so far.**