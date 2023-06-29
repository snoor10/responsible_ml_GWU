# RML6290:Group1 Home Mortgage Disclosure Act

### Team Members
Priyanka Bhatia (priyanka.bhatia@gwu.edu) 

Sadman Noor (snoor11@gwmail.gwu.edu) 

Mia Lakstigala  (mia.lakstigala@gwmail.gwu.edu)

Brenden Moore  (brendenmoore@gwmail.gwu.edu) 

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
