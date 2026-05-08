# 🚨 AI-Powered AML Transaction Monitoring & Risk Scoring System

# What is Anti Money Laundering (AML)?
  Anti-Money Laundering (AML) is the process of detecting and preventing criminals from making illegal money look legal.

Example:

A drug dealer earns ₹10 crore illegally.
He cannot directly put this money in a bank.

So he may:

split money into many small deposits
create fake companies
send money across countries
use crypto
create fake invoices
route money through multiple bank accounts

Goal: make “dirty money” look “clean”.

This is called money laundering.

AML systems try to detect this.

# Real-world Money Laundering Process 
1) Illegal money enters system.
2) Hide money trail. (India → Dubai → Singapore → shell company → crypto wallet) Tracking becomes hard.
3) Money becomes “clean”

# Who Needs AML?
1)Banks
2)Fintech companies
3)Crypto Exchanges
4) Government regulators

## Real-time Problems Faced in AML
 # a) Problem 1: Huge transaction volume

Big banks process millions of transactions daily.

Example:

10 million+ transactions/day
# b) Problem 2: Too many false positives
  System flags normal users.
# c) Problem 3: Criminal behavior changes
  Static rules fail.

Example:

Rule:
Flag transactions > ₹10 lakh

Criminal sends:

₹9.9 lakh repeatedly.

Rule bypassed.

## What Features AML Teams Want
   Core product requirements:

Detection Engine

Detect suspicious transactions.

Examples:

unusual transaction size
frequent transfers
velocity spikes

## 📌 Project Overview

Financial institutions process millions of transactions daily, making manual fraud detection inefficient and costly.  
This project simulates an **Anti-Money Laundering (AML) transaction monitoring system** that combines unsupervised anomaly detection and supervised risk modeling to identify and prioritize high-risk transactions.

The system demonstrates how machine learning can assist AML investigators in detecting suspicious behavior, reducing manual review workload, and improving fraud detection efficiency.

---

## 🎯 Business Problem

Fraud detection systems face several real-world challenges:

- Extremely imbalanced datasets (very few fraud cases)
- Evolving fraud patterns over time
- High operational cost of manual transaction reviews
- Risk of missing fraudulent transactions (false negatives)

This project addresses these challenges by:

- Detecting unusual transaction behavior using Isolation Forest
- Predicting fraud probability using XGBoost
- Assigning interpretable risk scores
- Monitoring model performance for stability and drift
- Simulating closed-loop retraining using investigator feedback

---

## 📊 Dataset

- Credit Card Fraud Detection Dataset (Kaggle)
- 284,807 transactions
- Fraud rate: ~0.17% (highly imbalanced)

This imbalance closely reflects real-world AML environments where fraudulent transactions are rare but high-impact.

---

## 🧠 System Architecture

Raw Transaction Data
↓
Data Preprocessing (Scaling & Split)
↓
Isolation Forest (Unsupervised Anomaly Detection)
↓
XGBoost Fraud Risk Model (Supervised Learning)
↓
Risk Score Generation & Categorization
↓
Performance Monitoring
↓
Closed-Loop Retraining Simulation


---

## 🔍 1️⃣ Unsupervised Anomaly Detection

Isolation Forest was implemented to identify unusual transaction patterns independent of fraud labels.

**Why this matters:**
- Captures suspicious behavior beyond historical fraud data
- Useful for detecting emerging fraud trends
- Enhances traditional rule-based monitoring

**Outputs:**
- Anomaly score
- Anomaly flag

---

## 🚀 2️⃣ Supervised Fraud Risk Model

An XGBoost classifier was trained to predict fraud probability using historical labeled data.

**Techniques applied:**
- Stratified train-test split
- Class imbalance handling using `scale_pos_weight`
- Evaluation using ROC-AUC, Precision, and Recall

### 📈 Model Performance

- ROC-AUC: **0.93+**
- Fraud Recall: **85–90%**
- Precision: **75–85%**

(*Replace with your actual results*)

The model was optimized for recall to minimize missed fraudulent transactions.

---

## 📈 3️⃣ Risk Scoring Framework

Model probabilities were converted into business-friendly risk scores:


Risk Score = Fraud Probability × 100


**Risk Categories:**

- Low Risk (0–30)
- Medium Risk (30–70)
- High Risk (70–100)

This enables prioritization of high-risk transactions for investigation teams.

---

## 📊 4️⃣ Monitoring Framework

To ensure performance stability, the following metrics were monitored:

- Precision
- Recall
- ROC-AUC
- Prediction distribution trends

Monitoring ensures early detection of model degradation and supports retraining decisions.

---

## 🔄 5️⃣ Closed-Loop Learning Simulation

The system simulates investigator feedback integration:

1. High-risk transactions are reviewed.
2. Confirmed labels are updated.
3. The model is periodically retrained.

This creates a feedback-driven AML intelligence cycle, improving detection performance over time.

---

## ⚠️ Challenges Faced

### 1️⃣ Severe Class Imbalance
Fraud cases represented less than 0.2% of the dataset.

**Solution:**
- Used ROC-AUC instead of accuracy
- Applied class weighting in XGBoost
- Focused on Recall optimization

---

### 2️⃣ Threshold Optimization
Default classification threshold (0.5) did not maximize fraud detection.

**Solution:**
- Evaluated multiple probability cutoffs
- Selected threshold balancing precision and recall

---

### 3️⃣ Interpreting Unsupervised Output
Isolation Forest does not directly classify fraud.

**Solution:**
- Compared anomaly flags with labeled fraud
- Used anomaly score as supplementary risk signal

---

## 💡 Business Impact

This system demonstrates how financial institutions can:

- Automate transaction monitoring
- Reduce manual investigation workload
- Improve fraud detection recall
- Detect emerging suspicious patterns
- Build adaptive, feedback-driven AML systems

---

## 🛠 Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Isolation Forest
- Matplotlib
- Joblib

---

## 📁 Project Structure

aml-risk-scoring-system/
│
├── data/ # Dataset (excluded from Git)
├── notebooks/ # Model development notebook
├── src/ # Modular ML scripts
├── models/ # Saved trained models (excluded from Git)
├── requirements.txt
├── README.md
└── .gitignore


---

## 🚀 Future Improvements

- Deploy model via FastAPI
- Add Streamlit dashboard for real-time scoring
- Integrate SHAP for model explainability
- Implement automated drift detection
- Simulate real-time transaction streaming

---

## 🏁 Conclusion

This project presents an end-to-end AML transaction monitoring framework combining supervised and unsupervised machine learning techniques to simulate real-world financial fraud detection systems.

It highlights the application of decision science principles in risk modeling, monitoring, and feedback-driven model improvement.

---

⭐ If you found this project interesting, feel free to star the repository!
