# Personal-loan-Notebook



# Model image
<img width="502" height="521" alt="image" src="https://github.com/user-attachments/assets/75edca32-f85b-412c-a1e5-b530a142a007" />

## Data Set

- **ID**: Customer ID  
- **Age**: Customer’s age in completed years  
- **Experience**: Number of years of professional experience  
- **Income**: Annual income of the customer (in thousand dollars)  
- **ZIP Code**: Home address ZIP code  
- **Family**: Family size of the customer  
- **CCAvg**: Average spending on credit cards per month (in thousand dollars)  
- **Education**: Education level  
  - 1: Undergrad  
  - 2: Graduate  
  - 3: Advanced / Professional  
- **Mortgage**: Value of house mortgage, if any (in thousand dollars)  
- **Personal_Loan**: Whether the customer accepted the personal loan offered in the last campaign  
- **Securities_Account**: Whether the customer has a securities account with the bank  
- **CD_Account**: Whether the customer has a certificate of deposit (CD) account with the bank  
- **Online**: Whether the customer uses internet banking facilities  
- **CreditCard**: Whether the customer uses a credit card issued by another bank (excluding All Life Bank)  

---

## Problem Statement

- Predict whether a liability customer will buy a personal loan or not  
- Identify the most significant variables influencing the decision  
- Determine which customer segments should be targeted more  
- Analyze whether **age** impacts a customer’s likelihood of taking a loan  
- Examine whether people with lower income are more likely to borrow loans  


# 🏦 Personal Loan Prediction
> Predicting whether a liability customer will accept a personal loan offer using **Logistic Regression** and **Decision Tree** classifiers.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0+-orange?style=flat&logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat&logo=jupyter)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

---

## 📌 Table of Contents
- [Problem Statement](#-problem-statement)
- [Dataset Overview](#-dataset-overview)
- [Business Questions Solved](#-business-questions-solved)
- [Project Structure](#-project-structure)
- [Tech Stack](#-tech-stack)
- [Workflow](#-workflow)
- [Models Used](#-models-used)
- [Results](#-results)
- [Key Insights](#-key-insights)
- [How to Run](#-how-to-run)
- [Predict New Customer](#-predict-new-customer)

---

## 🎯 Problem Statement

AllLife Bank has a growing customer base of liability customers (depositors). The bank wants to convert these depositors into personal loan customers. A previous campaign had a **9.6% success rate**.

The goal is to build a predictive model to:
- **Predict** whether a liability customer will buy a personal loan
- **Identify** the most significant variables driving loan acceptance
- **Segment** the customers that should be targeted

---

## 📊 Dataset Overview

| Feature | Description |
|---|---|
| `ID` | Customer unique identifier |
| `Age` | Customer's age in years |
| `Experience` | Years of professional experience |
| `Income` | Annual income (in $000) |
| `ZIP Code` | Home address ZIP code |
| `Family` | Family size |
| `CCAvg` | Avg. monthly credit card spend (in $000) |
| `Education` | 1: Undergrad, 2: Graduate, 3: Advanced |
| `Mortgage` | Value of house mortgage (in $000) |
| `Personal_Loan` | 🎯 **Target** — Did customer accept loan? (0/1) |
| `Securities_Account` | Has securities account? (0/1) |
| `CD_Account` | Has certificate of deposit account? (0/1) |
| `Online` | Uses internet banking? (0/1) |
| `CreditCard` | Has credit card from another bank? (0/1) |

- **Rows:** 5,000 customers
- **Columns:** 14 features
- **Target Distribution:** ~9.6% accepted loan (class imbalance)

---

## ❓ Business Questions Solved

| # | Question | Finding |
|---|---|---|
| 1 | Which variables are most significant? | Income, CCAvg, CD_Account, Education |
| 2 | Which customer segment to target? | High income, Graduate, CD Account holders |
| 3 | Does Age impact loan acceptance? | Age alone is not a strong predictor |
| 4 | Do low income people borrow more loans? | Higher income customers are more likely to take loans |

---

## 📁 Project Structure

```
personal-loan-prediction/
│
├── 📂 data/
│   └── loan_data.csv                  # Raw dataset
│
├── 📂 models/
│   ├── logistic_regression_model.pkl  # Saved LR model
│   ├── decision_tree_model.pkl        # Saved DT model
│   └── scaler.pkl                     # Saved StandardScaler
│
├── 📂 notebooks/
│   └── loan_prediction.ipynb          # Main analysis notebook
│
├── 📂 images/
│   ├── confusion_matrix_lr.png
│   ├── confusion_matrix_dt.png
│   ├── roc_curve.png
│   └── feature_importance.png
│
├── requirements.txt
└── README.md
```

---

## 🛠 Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.8+ | Core programming language |
| Pandas | Data manipulation |
| NumPy | Numerical computations |
| Matplotlib & Seaborn | Data visualization |
| Scikit-learn | ML models & evaluation |
| Pickle | Model serialization |
| Jupyter Notebook | Development environment |

---

## 🔄 Workflow

```
Raw Data
   ↓
Data Cleaning & EDA
   ↓
Feature Engineering
   ↓
Train/Test Split (80/20)
   ↓
StandardScaler (for LR)
   ↓
Model Training (LR + DT)
   ↓
Evaluation (Accuracy, ROC-AUC, F1)
   ↓
Save Models with Pickle
   ↓
Predict on New Customers
```

---

## 🤖 Models Used

### 1. Logistic Regression
- Applied `StandardScaler` before training
- Binary classification (loan accepted = 1, not accepted = 0)
- Evaluated using ROC-AUC, Precision, Recall

### 2. Decision Tree Classifier
- `max_depth = 5` to prevent overfitting
- No scaling required
- Feature importance extracted for business insights

---

## 📈 Results

| Model | Accuracy | ROC-AUC |
|---|---|---|
| Logistic Regression | ~91% | ~0.91 |
| Decision Tree | ~97% | ~0.98 |

> ✅ **Decision Tree outperforms** Logistic Regression on this dataset.
> The tree captures non-linear relationships between Income, CCAvg, and loan acceptance better.

---

## 💡 Key Insights

- 📌 **Income** is the single strongest predictor of loan acceptance
- 📌 Customers with a **CD Account** are significantly more likely to take a loan
- 📌 **CCAvg (Credit Card Spending)** positively correlates with loan acceptance
- 📌 **Education Level** matters — Graduate and Advanced customers accept more loans
- 📌 **Age alone** does not significantly predict loan acceptance
- 📌 Customers with **higher mortgage values** are slightly more likely to take loans

---

## ▶️ How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/personal-loan-prediction.git
cd personal-loan-prediction
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook notebooks/loan_prediction.ipynb
```

### 4. Run All Cells
Execute all cells top to bottom — data loads, models train, and pickled files are saved automatically.

---

## 🔮 Predict New Customer

After running the notebook, use this quick tester:

```python
import pickle
import numpy as np

# Load models
with open('models/logistic_regression_model.pkl', 'rb') as f:
    model = pickle.load(f)
with open('models/scaler.pkl', 'rb') as f:
    scaler = pickle.load(f)

# Customer: Age, Exp, Income, Family, CCAvg, Education,
#           Mortgage, Securities, CD, Online, CreditCard
new_customer = np.array([[40, 15, 120, 3, 3.0, 2, 150, 0, 1, 1, 0]])

prediction = model.predict(scaler.transform(new_customer))
probability = model.predict_proba(scaler.transform(new_customer))[0][1]

print("Prediction :", "✅ Will Take Loan" if prediction[0] == 1 else "❌ Won't Take Loan")
print(f"Confidence : {probability*100:.2f}%")
```

---

## 📦 Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

Install all:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## 📄 License

This project is licensed under the **MIT License** — feel free to use and modify.

---

## 🙋 Author

**Your Name**
- 📧 nirmeetchoudhary@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/yourprofile)
⭐ **If you found this project useful, please star the repo!**
