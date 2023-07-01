# DNSC 6290_11: Group1_Home Mortgage Disclosure Act

Group 1 spent Summer 2023 in DNSC 6920_11, taught by Professor Patrick Hall, developing interpretable machine learning models. The objective was to predict the probability of applicants being charged a higher rate than others for mortgages using the Home Mortgage Disclosure Act's historic mortgage reporting data. Due to the known dangers of deploying black-box machine learning models into public use where individuals care vulnerable to bias, our group worked with Professor Hall to develop explainable and interpretable predictive models that improve trust and encourage ethical decisions.

## Model Details

### Team Members
Priyanka Bhatia (priyanka.bhatia@gwu.edu) 

Sadman Noor (snoor11@gwmail.gwu.edu) 

Mia Lakstigala  (mia.lakstigala@gwmail.gwu.edu)

Brenden Moore  (brendenmoore@gwmail.gwu.edu) 

### Basic Information
- Model Date: June, 2023
- License: Apache 2.0
- Model implementation code: Assignment_5_Group_1

### Summary
The highest area under the curve (AUC) belonged to the EBM model with a value of 0.8253. Therefore, we chose the EBM (Explainable Boosting Machine) model as the best model among Generalized Linear Model (GLM), Monotonic Gradient Boosting (MXGB), and Explainable Boosting Machine (EBM) models. Bias testing was done by splitting the different groups like "Black", "Asian", "White", "Male", and "Female" and calculating the Adverse Impact Ratio (AIR) and Area Under the Curve (AUC). Model extraction attack was done via red-teaming. Lastly, sensitivity analysis (stress testing), residual analysis, and remediation (removing outliers and down-sampling to increase the signal from high-priced loans) were done to ensure model debugging.

### Intended use
* **Primary intended uses**
To reduce discrimination and bias in the process of issuing mortgage rates to applicants through the use of transparent explainable machine learning models. 
* **Primary intended users**
George Washington University Faculty, Students, Educators 
* **Out-of-scope use cases**
Models that appear in this repository are for educational-purposes and should not be used to determine real-world credit worthiness.

### Training data
* Home Mortgage Disclosure Act (HMDA) labeled training data.
  * **Source:**  https://github.com/jphall663/GWU_rml/tree/master/assignments/data 

* **Data Split Ratio:** Training Data (70%), Validation Data (30%).

* **Training data:** Rows = 112253, Columns = 23.

* **Validation data:** Rows = 48085, Columns = 23.

* **Definition of all the columns in training data:**
  
Row_id                       | Data Type | Variable Role | Description                                                  |
  | ---------------------------- | --------- | ------------- | ------------------------------------------------------------ |
  | black                        | Binary    | Input         | Applicants who are black (1) or not (0)                      |
  | asian                        | Binary    | Input         | Applicants who are Asian (1) or not (0)                      |
  | white                        | Binary    | Input         | Applicants who are white (1) or not (0)                      |
  | amind                        | Binary    | Input         | Applicants who are amind (1) or not (0)                      |
  | hipac                        | Binary    | Input         | Applicants who are Hipac (1) or not (0)                      |
  | hispanic                     | Binary    | Input         | Applicants who are Hispanic (1) or not (0)                   |
  | non_hispanic                 | Binary    | Input         | Applicants who are not Hispanic (1) or not (0)               |
  | male                         | Binary    | Input         | Gender of the applicant is male (1) or not (0)               |
  | female                       | Binary    | Input         | Gender of the applicant is female (1) or not (0)             |
  | agegte62                     | Binary    | Input         | Applicants' age is greater than 62 (1) or not (0)            |
  | agelt62                      | Binary    | Input         | Applicants' age is lower than 62 (1) or not (0)              |
  | term 360                     | Binary    | Input         | Whether the mortgage is a standard 360-month mortgage (1) or a different type of mortgage (0). |
  | conforming                   | Binary    | Input         | Whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc. |
  | debt_to_income_ratio_missing | Binary    | Input         | Missing marker (1) for std. debt to income ratio.            |
  | loan_amount_std              | Numeric   | Input         | Standardized amount of the mortgage for applicants.          |
  | loan_to_value_ratio_std      | Numeric   | Input         | Ratio of the size of the mortgage to the value of the applicant's property. |
  | no_intro_rate_period_std     | Binary    | Input         | Whether or not a mortgage includes an introductory rate period. |
  | intro_rate_period_std        | Numeric   | Input         | Standardized introductory rate period for mortgage applicants. |
  | property_value_std           | Numeric   | Input         | Value of the mortgaged property.                             |
  | income_std                   | Numeric   | Input         | Standardized income of the applicants.                       |
  | debt_to_income_ratio_std     | Numeric   | Input         | Standardized debt-to-income ratio of the applicants.         |
  | high_priced                  | Binary    | Target        | Whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages. |

#### Test data

* Home Mortgage Disclosure Act (HMDA) unlabeled test data.
  * **Source:** https://github.com/jphall663/GWU_rml/tree/master/assignments/data
* **Test data:** rows = 19831, columns = 22.
* **Difference:** Target Variable "High Priced" is not there in the Test Data.

#### Model details (in the best-remediated model)

* **Column(s) used as Inputs in Final Model:** 

  | Inputs                   |
  | ------------------------ |
  | income_std               |
  | conforming               |
  | term_360                 |
  | loan_amount_std          |
  | intro_rate_period_std    |
  | property_value_std       |
  | no_intro_rate_period_std |
  | debt_to_income_ratio_std |

* **Column(s) used as targets in the final model:** high_priced

* **The type of the best model:** Explainable Boosting Machine (EBM)

* **Software and the version:** Python 3.10.12, InterpretML v0.2.5.

### Quantitative analysis 

#### Model selection:
Our criteria for determining the best model is based on AUC. The higher AUC means the better model. Hence, we have chosen EBM as the best model based on the AUC of other models.
  
  | Model | AUC    |
  | ----- | ------ |
  | GLM   |.7538  |
  | MXGB  |.7917  |
  | EBM   |.8253  |

#### Local Feature importance across all models: 
Feature importance refers to techniques that assign a score to input features to quantify their utility at predicting a target variable.

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/bd07b58a2b80ab10523da1ba9161c6fcf8416cef/Model_card_Pic/Local%20Feature%20importance%20across%20all%20models.png)

#### Global Feature importance across all models: 
Global feature importance outlines which features are globally the most important for the model, it averages across all predictions we want to find the most important features and also quantify and rank this importance.

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/eb8577d7546d768162e100ca8ef9685f41f3a6cc/Model_card_Pic/Global%20Feature%20importance.png)

#### Partial Dependence Plots 
The partial dependence plots visualise the marginal effect of one or two features on the prediceted outcome of a machine learning model. 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/1ab9b4c31e8a8012685ff86c5f91661e341ef057/Model_card_Pic/Partial%20Dependence%20plots/PD_1.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/1ab9b4c31e8a8012685ff86c5f91661e341ef057/Model_card_Pic/Partial%20Dependence%20plots/PD_2.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_3.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_4.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_5.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_6.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_7.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_8.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_9.png)
![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/24a363bb589d9c0f7ce81eefdf3ff118f4c22608/Model_card_Pic/Partial%20Dependence%20plots/PD_10.png)

#### Grid search results Plot 
Grid search is a tuning technique that attempts to compute the optimum values of hyperparameters, in this project we used Grid Search to find a model with good accuracy and improved fairness. 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/b8ab386ce93d247c705275d6c58a14fe68701dd9/Model_card_Pic/Grid%20search.png)

#### Best AIR and AUC 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/980e5c03f6a97db2bfbf4088b35404196c570a46/Model_card_Pic/Best_auc-air.PNG)

#### Best model Hyperparameters 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/980e5c03f6a97db2bfbf4088b35404196c570a46/Model_card_Pic/Best%20model%20hyperparameters.PNG)

#### Model Extraction Attack 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/424d5d8dab1e007c0978cf237387c6ba51c7d82b/Model_card_Pic/Extraction_Attack.png)

#### Stolen Decision Tree Model

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/e1ddccc407062036fa63def85b47b05f4949ff12/Model_card_Pic/Stolen%20Decision%20Tree%20model.png)

#### Variable importance: H2O distributed Random Forest

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/e1ddccc407062036fa63def85b47b05f4949ff12/Model_card_Pic/Variable%20Importance%20for%20stolen%20model.png)

#### Sensitivity Analysis (Stress Testing) 

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/e1ddccc407062036fa63def85b47b05f4949ff12/Model_card_Pic/Sensitivity%20Analysis%20Stress%20Testing.png)

#### Residual Analysis
Residual plot used to identify outliers and improve model training

![alt text](https://github.com/snoor10/responsible_ml_GWU/blob/e1ddccc407062036fa63def85b47b05f4949ff12/Model_card_Pic/Residual%20analysis.png)

## Ethical Considerations 

- Model accuracy is vulnerable to changes in economic environment
- Data pre-processing should be evaluated for any legal issues as analysis utilizing racial data can be vulnerable to disparate treatment.
- Bias testing and remediation checks that models are assesing what they are targeting towards testing and external interference is not affecting the results. Inappropriate implementation of bias testing and remediation can lead to discrimination and societal harm.
- Despite our efforts to test and remediate our model for bias, elements of bias can remain. Therefore this model should be continually monitored for evidence of bias or other related issues. 


