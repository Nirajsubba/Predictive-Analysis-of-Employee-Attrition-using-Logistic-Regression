# Predictive-Analysis-of-Employee-Attrition-using-Logistic-Regression
Project Title: Predictive Analysis of Employee Attrition using Logistic Regression
1. Project Overview
This project aims to identify key factors driving employee turnover (attrition) within an organization. By applying machine learning to HR data, it provides actionable insights to help management develop targeted retention strategies, reduce turnover costs, and improve employee satisfaction.
2. Tools & Technologies Used
•	Programming Language: Python
•	Libraries:
o	pandas, numpy: For data manipulation and analysis.
o	matplotlib, seaborn: For comprehensive data visualization.
o	scikit-learn (sklearn): For machine learning (data preprocessing, model training, and evaluation).
•	Algorithm: Logistic Regression.
3. The Dataset (VA_Fn-UseC_HR-Employee-Attrition.csv)
•	The dataset contains information on 1,470 employees.
•	It comprises 35 features (attributes) for each employee, including:
o	Demographic: Age, Gender, Marital Status
o	Job-Related: Department, Job Role, Job Level, Overtime, Business Travel
o	Financial: Monthly Income, Daily Rate, Percent Salary Hike
o	Satisfaction Metrics: Job Satisfaction, Environment Satisfaction, Work-Life Balance
o	Tenure & Growth: Years at Company, Years Since Last Promotion, Total Working Years
•	Target Variable: Attrition (Yes/No) indicating whether the employee left the company.
4. Project Steps & Methodology
Step 1: Data Loading and Initial Inspection
•	The data is loaded and inspected using .head() and .info(), revealing the structure and data types (mix of integers and objects/categories).
Step 2: Data Preprocessing & Cleaning
•	Null Check: .isnull().sum() confirms there are no missing values in the dataset.
•	Descriptive Statistics: .describe() provides a summary of central tendency and distribution for numerical features.
Step 3: Exploratory Data Analysis (EDA) - The Core of Insight Generation
The EDA is extensive and broken into clear parts to uncover patterns:
•	1. Attrition Distribution: A countplot shows the severe class imbalance: a large majority of employees ("No") did not leave, while a small minority ("Yes") did.
•	2. Categorical Analysis: The project analyzes how attrition rates differ across categories like BusinessTravel, Department, JobRole, MaritalStatus, and OverTime. Key visual findings include:
o	Employees who work Overtime have a significantly higher attrition rate.
o	Sales Representatives and Laboratory Technicians show higher attrition.
o	Single employees attrite more than Married or Divorced colleagues.
o	The Sales and Human Resources departments experience higher turnover relative to Research & Development.
•	3. Numerical Analysis: Boxplots compare the distribution of numerical features (like Age, MonthlyIncome, YearsAtCompany) between employees who left and those who stayed. Key findings:
o	Employees who leave are generally younger.
o	They have a lower monthly income.
o	They have fewer years at the company and fewer years since their last promotion.
•	4. Correlation Heatmap: Identifies relationships between numerical variables. For example, MonthlyIncome is positively correlated with Age, JobLevel, and TotalWorkingYears (as expected).
Step 4: Data Preparation for Modeling
•	Dropping Irrelevant Features: EmployeeCount and EmployeeNumber are removed as they are unique identifiers and not predictive.
•	Target Encoding: The Attrition target is converted from "Yes"/"No" to 1/0.
•	Handling Categorical Variables: All categorical features (e.g., Department, JobRole) are converted into a numerical format using One-Hot Encoding (pd.get_dummies).
•	Train-Test Split: The data is split into training (90%) and testing (10%) sets. The stratify parameter is crucial here to maintain the same attrition ratio in both sets, ensuring the model learns from the imbalanced data effectively.
•	Feature Scaling: Numerical features are standardized using StandardScaler for Logistic Regression, which is sensitive to the scale of input data.
Step 5: Model Building and Training
•	Algorithm Choice: Logistic Regression. This is a interpretable model well-suited for binary classification problems (leave/stay) and, most importantly, it provides coefficients that explain the impact of each feature on the outcome.
•	The model is trained (.fit()) on the scaled training data.
Step 6: Model Evaluation and Interpretation
The trained model is evaluated on the unseen test set.
•	Confusion Matrix & Classification Report:
o	The model achieves 86% overall accuracy.
o	Precision for Class 1 (Attrition): 0.64 - When the model predicts attrition, it is correct 64% of the time.
o	Recall for Class 1 (Attrition): 0.29 - The model identifies only 29% of all employees who actually left. This low recall is a common challenge in imbalanced datasets but is critical for HR to catch at-risk employees.
o	F1-Score: 0.40 - The harmonic mean of precision and recall, indicating a trade-off between the two.
o	ROC AUC Score: 0.787 - Shows the model's ability to distinguish between the two classes is good (better than random guessing, which is 0.5).
5. Key Findings & Business Impact
The Most Significant Drivers of Attrition (from Model Coefficients):
•	Strongest Positive Correlations (Increased Likelihood of Leaving):
o	OverTime_Yes: Working overtime is the strongest predictor of attrition.
o	BusinessTravel_Travel_Frequently: Frequent travel is highly correlated with leaving.
o	YearsSinceLastPromotion: Employees who haven't been promoted in a long time are more likely to leave.
•	Strongest Negative Correlations (Decreased Likelihood of Leaving):
o	TotalWorkingYears and YearsInCurrentRole: More experienced employees and those stable in their roles are less likely to leave.
o	EnvironmentSatisfaction and JobSatisfaction: Higher satisfaction levels are strongly associated with employee retention.
Actionable Recommendations for HR:
1.	Review Overtime Policies: Actively manage workloads to reduce mandatory overtime and compensate fairly for it.
2.	Manage Travel: For frequent travelers, ensure travel is compensated and manageable to prevent burnout.
3.	Implement Structured Career Paths: Create clear promotion schedules and development opportunities to address stagnation (YearsSinceLastPromotion).
4.	Focus on Satisfaction: Regularly measure and act upon employee satisfaction surveys to improve EnvironmentSatisfaction and JobSatisfaction.
5.	Targeted Interventions: Use the model's predictors to identify employees at high risk of leaving and conduct proactive stay interviews.
6. Conclusion
This project successfully transitioned from raw HR data to actionable business intelligence. While the Logistic Regression model's recall for attrition can be improved (e.g., by using techniques like SMOTE or trying different algorithms like Random Forest), its true value lies in its interpretability. The analysis clearly pinpoints the specific factors that most significantly impact employee turnover, empowering HR and management to make data-driven decisions to foster a more stable and satisfied workforce.

