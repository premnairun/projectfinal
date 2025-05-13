# projectfinal
# UN Recruitment Data Analysis: Comprehensive README

## Project Overview

### Purpose
This project analyzes UN recruitment data to:
- Identify diversity gaps in applicant pools
- Optimize hiring processes
- Develop predictive models for application success
- Provide actionable recommendations for achieving gender parity

### Key Findings
1. **Gender Disparities**  
   - Only 30% female applicants in technical roles vs 70% male
   - Gender shows moderate correlation (-0.20) with application rates

2. **Model Performance**  
   - Initial models achieved **94% accuracy** (Logistic Regression/Random Forest)
   - After hyperparameter tuning, maintained **94% accuracy** with improved robustness
   - Best model: Random Forest (AUC: 0.983)

3. **Process Insights**  
   - High-competition jobs receive 2,398±512 applications
   - Application success strongly correlates with experience (r=0.62)

## Detailed Notebook Structure

### 1. Data Cleaning & EDA
- Handled missing values in categorical fields
- Standardized job family classifications
- Visualized distributions:
  - Job families (LAN/ADM dominant)
  - Gender imbalance (2:1 male:female in tech)
  - Top nationalities (KEN, IND, USA leading)

### 2. Feature Engineering
- Created key metrics:
  - `APPLICATIONS_PER_JOB`: Mean = 1,602 (±513)
  - `DAYS_TO_APPLY`: Median = 14 days
- Encoded categorical variables (Job Family, Nationality)

### 3. Correlation Analysis
- Strongest predictors:
  - Years of experience (r=0.62)
  - Education level (r=0.55)
- Gender showed weak correlations with other features

### 4. Clustering Analysis
Identified 3 distinct job clusters:
1. **High-Competition** (41% of jobs)
   - 2,398 avg applications
   - 65% male applicants
2. **Specialized** (35%)
   - Requires 10+ years experience  
3. **Entry-Level** (24%)
   - Fastest hiring cycle (23 days)

### 5. Modeling & Hyperparameter Tuning
#### Initial Models:
| Model                | Accuracy | ROC-AUC |
|----------------------|----------|---------|
| Logistic Regression  | 0.94     | 0.983   |
| Random Forest        | 0.94     | 0.983   |

#### After Tuning:
- **Optimal Parameters Found:**
  ```python
  {'max_depth': 20, 
   'min_samples_leaf': 2,
   'min_samples_split': 5,
   'n_estimators': 200}
  ```
- **Post-Tuning Performance:**
  - Maintained 94% accuracy
  - Improved feature importance clarity
  - Reduced overfitting risk

### 6. Findings & Recommendations
**Immediate Actions:**
- Implement blind screening for 20% of technical roles
- Set 40% minimum female shortlist rate for STEM positions

**Long-Term:**
- Develop skills-based assessments for technical roles
- Create LDC recruitment pipeline

## How to Run This Analysis

### Requirements
```bash
Python 3.12
```
**Requirements.txt:**
```
pandas
scikit-learn
matplotlib
seaborn
jupyter
```

### Execution Steps
1. **Data Preparation:**
   ```bash
   # Place your data file in input/ folder
   ```

2. **Run the Notebook:**
   ```bash
   jupyter notebook main.ipynb
   ```
   - Execute all cells sequentially
   - Model tuning may take 10-15 minutes (depending on hardware)

## Technical Notes

### Model Performance Details
- **Why 94% Accuracy Persisted:**
  - Data has clear separable patterns
  - Additional tuning improved generalizability without changing accuracy
  - Current performance is likely near the data's theoretical limit

### Limitations
1. **Data Constraints:**
   - Lacks salary band information
   - No applicant feedback data
2. **Model Caveats:**
   - High accuracy may reflect data leakage risk
   - Requires quarterly retraining

## References & Acknowledgments

### Data Sources
- UN HR Department (2023)
- World Bank Country Classification

### Methodological References
1. Scikit-learn: Pedregosa et al., JMLR 12 (2011)
2. XGBoost: Chen & Guestrin, KDD '16
