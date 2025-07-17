# AI-Assignment-Week-5

Part 1: AI Workflow Design (30 points)
1. Problem Definition (6 points)
Hypothetical AI Problem: Predicting student dropout rates in a university setting.

Objectives:

Identify students at risk of dropping out early in the semester.

Enable targeted intervention by academic advisors.

Reduce overall dropout rate by 15% over two academic years.

Stakeholders:

University administration

Students

KPI: Percentage reduction in dropout rates after intervention.

2. Data Collection & Preprocessing (8 points)
Data Sources:

Student academic records (grades, attendance)

Survey data on mental health and financial background

Potential Bias: Students who do not respond to surveys may be underrepresented, skewing results toward certain demographics.

Preprocessing Steps:

Handle missing data using mean imputation or deletion depending on missingness level.

Normalize numerical features (e.g., GPA).

Encode categorical variables (e.g., course major) using one-hot encoding.

3. Model Development (8 points)
Chosen Model: Random Forest – robust to overfitting and works well with tabular data and mixed feature types.

Data Split:

70% training

15% validation

15% test

Hyperparameters to Tune:

Number of trees – affects bias-variance trade-off.

Maximum depth – controls overfitting.

4. Evaluation & Deployment (8 points)
Evaluation Metrics:

Accuracy – measures overall correctness.

Recall – important to identify as many at-risk students as possible.

Concept Drift: When the relationship between features and labels changes over time (e.g., new online learning policies).
Monitoring Strategy: Scheduled model retraining and performance tracking on recent data.

Deployment Challenge: Scalability – serving predictions to thousands of students simultaneously during registration season.

Part 2: Case Study Application – Hospital Readmission Risk (40 points)
Problem Scope (5 points)
Problem: Predict whether a patient will be readmitted within 30 days of discharge.

Objectives:

Flag high-risk patients for extra care before discharge.

Reduce hospital readmission rates and associated costs.

Stakeholders:

Hospital administrators

Healthcare providers (doctors, nurses)

Data Strategy (10 points)
Data Sources:

Electronic Health Records (EHRs) – diagnoses, treatments, vitals.

Patient demographics – age, gender, socioeconomic data.

Ethical Concerns:

Patient privacy and data protection.

Risk of biased predictions for minority groups.

Preprocessing Pipeline:

Handle missing values in vitals using interpolation.

One-hot encode categorical features (e.g., diagnosis codes).

Feature engineering: create new features such as "days since last admission" or "number of previous admissions."

Model Development (10 points)
Model: Logistic Regression – interpretable and effective for binary classification in clinical settings.

Hypothetical Confusion Matrix:

Predicted Readmit	Predicted No Readmit
Actual Readmit	40	10
Actual No Readmit	20	130

Precision: 40 / (40 + 20) = 0.67

Recall: 40 / (40 + 10) = 0.80

Deployment (10 points)
Integration Steps:

Containerize the model with Docker.

Expose a REST API endpoint.

Integrate into hospital’s EHR system for real-time use.

Regulatory Compliance:

Use anonymized data for model training.

Implement audit trails for model predictions (required by HIPAA).

Perform regular security audits and access control.

Optimization (5 points)
Overfitting Mitigation Strategy: Use dropout regularization or limit tree depth (if using tree-based models), and cross-validation to ensure generalization.

Part 3: Critical Thinking (20 points)
Ethics & Bias (10 points)
Bias Impact: Biased data may overpredict risk for certain ethnic or age groups, leading to unnecessary intervention or neglect.

Bias Mitigation Strategy:
Use IBM AI Fairness 360 toolkit to audit and correct biases in the model pipeline (e.g., apply reweighting or adversarial debiasing).

Trade-offs (10 points)
Interpretability vs Accuracy:
Interpretable models like logistic regression are preferred in healthcare for trust and regulatory reasons, even if slightly less accurate than black-box models like deep neural networks.

Resource Limitation Impact:
If computational resources are limited, lighter models (e.g., decision trees or logistic regression) are preferable over deep learning models that require GPUs and large memory.

Part 4: Reflection & Workflow Diagram (10 points)
Reflection (5 points)
Challenge: Balancing accuracy with interpretability, especially when model suggestions affect patient care.

Improvement Strategy:
With more time, conduct feature importance analysis and stakeholder feedback loops to improve both model performance and trust.

Workflow Diagram (5 points)
plaintext

Problem Definition
      ↓
Data Collection
      ↓
Data Preprocessing
      ↓
Model Selection & Training
      ↓
Model Evaluation
      ↓
Deployment
      ↓
Monitoring & Feedback

