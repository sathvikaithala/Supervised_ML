# Credit Risk Evaluation - Supervised Machine Learning
UC Berkeley Extension Data Analytics Boot Camp Module 17

---

## Objectives
The objective of this module was to learn about supervised machine learning algorithms and resampling to attempt to address class imbalances. We used various resampling techniques to determine credit worthiness of various customers. This analysis was done in the *credit_risk_resampling.ipynb* notebook.


## Data
Our data is stored in "LoanStats_2019Q1.csv" in the Resources folder. It houses data from LendingTree for thousands of loan applications. 

## Contents
|Folder|Description|
|------|-----------|
|Resources|Contains data for both the module and challenge notebooks|
|ModuleFiles|Contains notebooks created throughout the module|
|ChallengeFiles|Contains notebooks created for the Challenge portion of the module|
|Images|Screenshots of confusion matrices and reports that are used in the writeup|


## Resampling Techniques - (credit_risk_resampling.ipynb)
1) Naive Random Oversampling
2) SMOTE Oversampling
3) Undersampling
4) Combination Sampling (SMOTEENN)

---

### Naive Random Oversampling
In Naive Random Oversampling, class imbalances are handled by duplicating the existing data in the minor class. In this dataset, the minor class is defined by high risk loan applications, and the major class is made up of low risk loan applications.  

##### Confusion Matrix and Classification Report
![Naive Random Oversampling](Images/naive_oversampled.png)

**Balanced Accuracy Score: 0.623**

We found that the precision for the low-risk loans (major class) was 1.00, and the precision for the high-risk loans (minor class) was very low -- 0.01.

Recall values for the low-risk loans and high-risk loans were almost the same (0.62 low-risk vs. 0.63 high-risk). 

The balanced accuracy score of 0.623 is not phenomenal, but it is among the highest we observed.

---

### SMOTE Oversampling
As in Naive Random Oversampling, SMOTE Oversampling creates data to allow the minor class to match the major class in size. It does so by interpolating data using k-nearest-neighbors rather than simply duplicating data.

##### Confusion Matrix and Classification Report
![SMOTE Oversampling](Images/smote_oversampled.png)

**Balanced Accuracy Score: 0.624**

We found that the precision values matched those we got in the Random Naive Oversampling method. 

Recall values are similar in this case as well (0.65 low-risk vs 0.6 high-risk). 

The balanced accuracy score of 0.624 is also very similar to the score achieved in Random Naive Oversampling.

---

### Undersampling
Undersampling operates on principles opposite of what we see in oversampling. Rather than creating duplicates of existing data, it only utilizes *actual, existing* data. However, this means that some data is removed in order to achieve this.

##### Confusion Matrix and Classification Report
![Undersampling](Images/undersampled.png)

**Balanced Accuracy Score: 0.488**

The precision values of the undersampling model are similar to our other models -- very poor for high-risk application detection.

Recall values for this method underperformed the other methods we tried (0.42 low-risk, 0.55 high-risk).

The balaned accuracy score of 0.488 is the lowest among all four of our methods.

---

### Combination Sampling
Combination Sampling (in this case, SMOTEENN Sampling), is a middle ground between over- and under-sampling methods.

##### Confusion Matrix and Classification Report
![SMOTEENN Combination Sampling](Images/smoteenn.png)

**Balanced Accuracy Score: 0.622**

The precision values for our Combination Sampling model are similar to all of our other models -- 0.01 for high-risk class, and 1.00 for the low-risk class.

While the recall values are not great, they are among the highest of our cohort for the high-risk class (0.55 low-risk, 0.7 high-risk).

The balanced accuracy score of 0.622 is similar to both our Naive Random Oversampling and SMOTE Oversampling methods.

---

### Summary, Analysis, and Recommendation

The F1 values for all four resampling models is very poor, at 0.01 to 0.02 for the high-risk class. 

Balanced accuracy scores are also similar for the Random Naive Oversampling, SMOTE Oversampling, and SMOTEENN Combination Sampling methods (ranging from 0.622-0.624). The Undersampled method underperformed in this regard, with a balanced accuracy score of only 0.488.

Of the methods utilized in this module, I would not recommend any of them, as the accuracy scores are not strong enough to inspire confidence in the model's ability to accurately determine a high-risk credit application. However, if one of these models had to be chosen, I would suggest using the SMOTEEN Combination model, since it has the highest recall value (0.7) for high-risk applications and a balanced accuracy score similar to our better performing models (0.622).

---


