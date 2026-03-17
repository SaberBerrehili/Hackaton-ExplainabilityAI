#  Technical Documentation — HACKATHON EXPLAINABILITYAI

##  Team 11
Olivier YERRO  
BERREHILI Saber  
DOAN HUU Xuan  
SEGUIN Thierry  
SYASSI Imad  

---

##  Project Overview

This project aims to develop a machine learning model to predict employee turnover using HR data.  
The objective is to assist Human Resources in identifying employees at risk of leaving the company.

The prediction is based on the binary target variable:

- `Termd = 0` → Employee still in the company  
- `Termd = 1` → Employee has left  

---

##  Dataset

- Dataset: `HRDataset_v14.csv`
- Size: 311 rows
- Type: Structured HR data (tabular)
- Task: Binary classification

### Key Features
- Salary
- Department
- Position
- PerformanceScore
- EngagementSurvey
- Absences
- DaysLateLast30

---

##  Data Preprocessing

The dataset was cleaned and transformed before modeling.

###  Columns Removed

**Leakage (directly related to departure):**
- `TermReason`
- `DateofTermination`
- `EmploymentStatus`
- `EmpStatusID`

**Personal / Identifying data:**
- `Employee_Name`
- `EmpID`
- `ManagerName`

**Redundant / ID columns:**
- `MaritalStatusID`
- `DeptID`
- `PerfScoreID`
- `PositionID`
- `GenderID`

**Sensitive attributes (ethical reasons):**
- `Sex`
- `RaceDesc`
- `HispanicLatino`

---

###  Feature Engineering

We created a new feature:

- **`seniority`**  
  Represents the employee's tenure in the company.

Calculation:
- If still employed → `today - DateofHire`
- If left → `DateofTermination - DateofHire`

---

##  Model

### Model Used: Random Forest Classifier

We used a Random Forest model due to its robustness and effectiveness on tabular datasets.

### Why Random Forest?

- Handles non-linear relationships
- Works well with mixed data types
- Resistant to overfitting (ensemble method)
- Good performance without heavy tuning

📚 Documentation:  
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html

---

##  Training & Evaluation

- Train/Test split: **70% / 30%**
- No cross-validation (time constraint)
- Evaluation metrics:
  - Accuracy
  - Precision
  - Recall
  - F1-score

📚 Metrics documentation:  
https://scikit-learn.org/stable/modules/model_evaluation.html

---

## Ethical Considerations

To reduce the risk of bias and discrimination:

- Sensitive features (`Sex`, `RaceDesc`, `HispanicLatino`) were removed from the model
- The model is designed as a **decision-support tool**, not an automated decision system

📚 Fairness concepts (Google ML Guide):  
https://developers.google.com/machine-learning/crash-course/fairness/what-is-fairness

---

##  Cybersecurity & Data Protection

- Personal identifiers were removed from the dataset
- Sensitive attributes were excluded from modeling
- Dataset exploration was limited (only first rows displayed)

Note:  
The dataset is currently included in the repository.  
As a best practice, it would be preferable to:
- remove it from the repo, or
- clearly indicate that it is synthetic and anonymized

📚 GDPR overview:  
https://gdpr.eu/what-is-gdpr/

---

## Data Analysis & Visualization

We used:

- **Pandas** for data manipulation  
- **Seaborn / Matplotlib** for visualization  
- Correlation matrix to explore relationships between variables  

📚 Pandas documentation:  
https://pandas.pydata.org/docs/

📚 Seaborn documentation:  
https://seaborn.pydata.org/

---

##  Tools & Environment

- Python (Google Colab / Jupyter Notebook)
- Scikit-learn
- Pandas
- NumPy
- Matplotlib / Seaborn

📚 Scikit-learn documentation:  
https://scikit-learn.org/stable/

---

##  Limitations

- Small dataset (311 rows)
- Synthetic dataset → not fully representative of real-world HR data
- No cross-validation
- Possible hidden biases in historical data
- Correlation ≠ causation

---

##  Conclusion

This project demonstrates how machine learning can support HR decision-making while addressing ethical and cybersecurity challenges.

The model provides useful insights but must be used with caution and always under human supervision.

---

## References

- Scikit-learn Random Forest:  
  https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html  

- Model evaluation:  
  https://scikit-learn.org/stable/modules/model_evaluation.html  

- Fairness in ML:  
  https://developers.google.com/machine-learning/crash-course/fairness/what-is-fairness  

- Pandas documentation:  
  https://pandas.pydata.org/docs/  

- GDPR overview:  
  https://gdpr.eu/what-is-gdpr/  
