# RML6290:Group1 Home Mortgage Disclosure Act

### Team Members
Priyanka Bhatia (priyanka.bhatia@gwu.edu) 

Sadman Noor (snoor11@gwmail.gwu.edu) 

Mia Lakstigala  (mia.lakstigala@gwmail.gwu.edu)

Brenden Moore  (brendenmoore@gwmail.gwu.edu) 

### License
Apache-2.0 license

### Summary
The highest area under the curve (AUC) belonged to the EBM model with a value of 0.8253. Therefore, we chose the EBM (Explainable Boosting Machine) model as the best model among Generalized Linear Model (GLM), Monotonic Gradient Boosting (MXGB), and Explainable Boosting Machine (EBM) models. Bias testing was done by splitting the different groups like "Black", "Asian", "White", "Male", and "Female" and calculating the Adverse Impact Ratio (AIR) and Area Under the Curve (AUC). Model extraction attack was done via red-teaming. Lastly, sensitivity analysis (stress testing), residual analysis, and remediation (removing outliers and down-sampling to increase the signal from high-priced loans) were done to ensure model debugging.

### Intended use
* **Primary intended uses**
*Need to discuss
* **Primary intended users**
*Need to discuss
* **Out-of-scope use cases**
*Need to discuss

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

#### Evaluation data

* Home Mortgage Disclosure Act (HMDA) unlabeled test data.
  * **Source:** https://github.com/jphall663/GWU_rml/tree/master/assignments/data
* **Test data:** rows = 19831, columns = 22.
* **Difference:** Target Variable "High Priced" is not there in the Test Data.

#### Model details (in the best-remediated model)

* **Inputs:** 

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

* **Target:** high_priced

* **The type of the best model:** Explainable Boosting Machine (EBM)

* **Software and the version:** needs to discuss

* **Hyperparameters:** 

  | Best Model Hyperparameters | Value |
  | -------------------------- | ----- |
  | max_bins                   |    |
  | max_interaction_bins       |     |
  | interactions               |      |
  | outer_bags                 |      |
  | inner_bags                 |      |
  | learning_rate              |  |
  | validation_size            |    |
  | min_samples_leaf           |     |
  | max_leaves                 |      |



#### Quantitative analysis 

* **Model selection:** Our criteria for determining the best model is based on AUC. The higher AUC means the better model. Hence, we have chosen EBM as the best model based on the AUC of other models.
  
  | Model | AUC    |
  | ----- | ------ |
  | GLM   |.7538  |
  | MXGB  |.7917  |
  | EBM   |.8253  |

* **Feature importance**: The best EBM feature importance plot shows global variable importance in EBM to make a feature selection.

  
