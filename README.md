# Fraudulent-Firm-Detection
## Background & Objective
**Background**: 
<br>
This project has been taken up as a research work for a case study of an external government audit company. During audit-planning, auditors examine the business of different government offices but the target to visit the offices with very-high likelihood and significance of misstatements. This is calculated by assessing the risk relevant to the financial reporting goals (Houston, Peters, and Pratt 1999)
<br><br>
**Objective**:
<br>
Building a predictive model that can be used to classify a firm as fraudulent or not
## Problem Statement
**Goal**:
<br>
Building a predictive model that can be used to classify a firm as fraudulent or not
<br><br>
**Research Question**:
<br>
How to predict fraudulent firms using historical data?
<br><br>
**Businnes Benefit**:
<br>
Auditor are able to maximize the field-testing work of high-risk firms
that warrant significant investigation.
<br><br>
**Expected Outcome**:
<br>
Predictive model with low recall/sensitivity that able to classify whereas a firm fraudulent or not
## Data Source
The data was taken from Audit data data set source from UCI Machine Learning Library: 
<br>
https://archive.ics.uci.edu/ml/datasets/Audit+Data
<br>
<br>
Dataset contain exhaustive one year non-confidential data in the year 2015 to 2016 of firms is collected from the Auditor Office of India to build a predictor for classifying suspicious firms.
<br>
<br>
It was mention in UCI Machine Learning Library that the data was taken for the purpose of research and was publish in Applied Artificial Intelligence 32.1 (2018). Below attached citation pertaining the research:
<br>
<b>Hooda, Nishtha, Seema Bawa, and Prashant Singh Rana. 'Fraudulent Firm Classification: A Case Study of an External Audit.' Applied Artificial Intelligence 32.1 (2018): 48-64.</b>
## Data Dictionary
The dataset contain two csv file called audit_risk and trial. Little info about the data, audit_risk has 27 column whereas trial has 18 column. The description upon each feature in audit_risk will be mention below:

* `Sector_Score` – Historical risk score value for each target sector
* `LOCATION_ID` – Unique ID of the city or province
* `PARA_A` - Discrepancy found in the planned expenditure of inspection and summary report A in Rs (in crore)
* `SCORE_A, RISK_A` – These columns can be derived from the PARA_A
* `PARA_B` - Discrepancy found in the unplanned expenditure of inspection and summary report B in Rs (in crore)
* `SCORE_B, RISK_B` - These columns can be derived from the PARA_B. 
* `TOTAL` - Total amount of discrepancy found in other reports Rs (in crore)
* `numbers` - Historical discrepancy score
* `Score_B.1, Risk_C` - These columns can be derived from the numbers
* `Money_Value` - Amount of money involved in misstatements in the past audits
* `SCORE_MV, Risk_D` - These columns can be derived from the Money_Value
* `District_Loss` - Historical risk score of a district in the last 10 years
* `PROB` – probability of District_Loss
* `Risk_E` – It is the product of District_Loss and PROB
* `History` - Average historical loss suffered by firm in the last 10 years
* `Prob` – Probability of Historical Loss score
* `Risk_F` – It is the product of History and prob
* `Score` – It is a deciding factor in classifying a firm as ‘Fraud’ or ‘Not Fraud’, In the trial file, if the score is less than or equal to 2, the firm is labelled ‘Not Fraud’, if it is greater than 2, it is labelled ‘Fraud’
* `Inherent_Risk` - the risk present due to the discrepancies present in the transactions
* `CONTROL_RISK` - the risk due to the discrepancies which are left undetected by an internal control system
* `Detection_Risk` - risk of discrepancies present in the firm which are not even detected by the audit procedures
* `Audit_Risk` – It is the product of Inherent, control and detection risks
* `Risk` – It is dependent on Audit_Risk, If the Audit_Risk is less than or equal to 1, the firm is labelled ‘Not Fraud’ and if it is greater than 1, it is labelled ‘Fraud’.
<br>
<br>

Notes pertaining the difference between trial and audit_risk dataset:
<br>
1. The Score_A in Audit_Risk multiplied by 10 is the Score_A in trial. The same applies to Score_B. 
2. Audit_Risk dataset contains Risk_A(a derivative of PARA_A and Score_A) and Risk_B(a derivative of PARA_B and Score_B) which are not present in trial. 
3. TOTAL and numbers columns are identical in Audit_Risk and trial. 
4. Score_B.1 multiplied by 10 is the Marks column in trial. 
5. Audit_Risk has an extra column Risk_C( a derivative of numbers and Score_B.1) compared to trial. 
6. Score_MV in Audit_Risk multiplied by 10 is the Money_Marks column in trial dataset. 
7. Risk_D( a derivative of Money_Value and Score_MV) is absent in trial. 
8. PROB(probability of district loss score) in Audit_Risk multiplied by 10 is the Loss_Score in trial.
9. prob(probability of historical loss score) in Audit_Risk multiplied by 10 is the History_Score in trial. 
10. Score is exactly identical in both Audit_risk and trial datasets. 
11. Risk column in trial is calculated based on Score value. 
12. The discrepancy in the Risk columns of Audit_Risk and trial datasets arises from the fact that Audit_Risk dataset uses Audit_Risk column(Product of Inherent_Risk, Controlled_Risk and Detection_Risk columns) to classify a firm as Fraud or otherwise.
## Conclusion
* The decision tree model is the recommended model to be used compared to the 5 models tested because it produces the largest recall value
* Using recall parameter in confusion matrix we caan conclude that on average every 1000 institution that truly doing fraudulent act, there were 1000-961 = 39 institution that failed to be predicted that they were doing fraudulent act
* "Money Value, District, PARA_A, PARA_B" are the feature that contribute the most in the model
