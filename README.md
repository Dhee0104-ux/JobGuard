# 🛡️ JobGuard — AI-Powered Fake Job & Scam Detection

> An NLP + Machine Learning system that analyzes job postings and identifies potentially fraudulent or scam job advertisements.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange)
![NLP](https://img.shields.io/badge/NLP-TF--IDF-green)
![UI](https://img.shields.io/badge/UI-Gradio-purple)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Ready-yellow?logo=googlecolab)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Overview

**JobGuard** is an AI-powered fake job detection system designed to help job seekers identify potentially fraudulent job postings.

Online job scams can contain suspicious patterns such as:

- Unrealistic salary promises
- Guaranteed employment
- No-interview hiring
- Registration or processing fees
- Requests for bank details
- Requests for OTPs
- Cryptocurrency payments
- Urgent recruitment messages
- Fake work-from-home opportunities
- Requests for sensitive personal information

JobGuard analyzes the textual content of a job posting using **Natural Language Processing (NLP)** and **Machine Learning** and produces:

- 🟢 Likely Legitimate
- 🟡 Medium Risk
- 🟠 High Risk
- 🔴 Very High Risk
- 🚨 Potential Job Scam

The project also provides an interactive **Gradio web interface** that can be run directly in Google Colab.

---

# ✨ Features

### 🔍 Single Job Scanner

Enter:

- Job title
- Company
- Location
- Employment type
- Job description

JobGuard analyzes the posting and generates a scam-risk assessment.

---

### 🤖 Machine Learning Detection

The system uses:

**TF-IDF + Logistic Regression**

TF-IDF converts job-posting text into numerical features, while Logistic Regression learns patterns associated with legitimate and fraudulent postings.

---

### 📊 Scam Probability

JobGuard provides an estimated probability:

```text
0% ─────────────────────────────── 100%

Low       Medium       High       Very High
🟢          🟡           🟠           🔴
```

Example:

```text
Scam Probability: 87.42%

Verdict:
🚨 POTENTIAL JOB SCAM
```

---

### 🧠 Explainable Predictions

The system displays important words and phrases that influenced the model.

Examples:

```text
registration fee
bank details
no interview
guaranteed income
urgent
Telegram
```

This makes the model easier to understand instead of providing only a black-box prediction.

---

### 📂 Custom Dataset Training

Users can upload their own:

- `.csv`
- `.xlsx`

dataset.

JobGuard automatically attempts to detect common target columns such as:

```text
fraudulent
fraud
scam
label
target
fake
```

It also automatically combines available text fields such as:

```text
title
description
company_profile
requirements
benefits
location
```

---

### 📋 Batch Job Scanning

Users can upload a dataset containing hundreds or thousands of job postings.

JobGuard generates:

```text
JobGuard_Prediction
Scam_Probability
Risk_Level
```

The results can then be exported as a CSV file.

---

### 📈 Model Evaluation

The project calculates:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC AUC

It also generates:

- Confusion Matrix
- Model Performance Chart
- Feature Importance Chart

---

### 🎨 Interactive Dashboard

The application contains multiple sections:

```text
🔍 Scan a Job
📂 Train Custom Dataset
📊 Batch Scanner
📈 Model Performance
🧠 How It Works
```

The entire interface is powered by **Gradio**.

---

# 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │    Job Posting      │
                    │                     │
                    │ Title               │
                    │ Company             │
                    │ Description         │
                    │ Location            │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Text Cleaning     │
                    │                     │
                    │ Lowercase           │
                    │ Remove URLs         │
                    │ Remove HTML         │
                    │ Normalize Text      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      TF-IDF         │
                    │                     │
                    │ Unigrams + Bigrams  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Logistic Regression │
                    │      Classifier      │
                    └──────────┬──────────┘
                               │
                               ▼
                 ┌────────────────────────────┐
                 │      Prediction Engine     │
                 └─────────────┬──────────────┘
                               │
               ┌───────────────┴────────────────┐
               ▼                                ▼
       ┌─────────────────┐              ┌──────────────────┐
       │ Scam Probability│              │   Classification │
       │                 │              │                  │
       │ 0% — 100%       │              │ Legitimate       │
       └────────┬────────┘              │ Potential Scam   │
                │                       └────────┬─────────┘
                └──────────────┬────────────────┘
                               ▼
                    ┌─────────────────────┐
                    │   Gradio Dashboard  │
                    │                     │
                    │ Risk Level          │
                    │ Explanation         │
                    │ Visualizations      │
                    └─────────────────────┘
```

---

# 🧠 Machine Learning Pipeline

## 1. Data Collection

Job postings are collected from a labeled dataset containing legitimate and fraudulent job advertisements.

---

## 2. Text Preprocessing

The text is cleaned using:

- Lowercasing
- URL removal
- Email removal
- HTML removal
- Special-character removal
- Whitespace normalization

Example:

```text
"URGENT!!! Earn $5000 DAILY!!! Apply at www.example.com"
```

becomes approximately:

```text
"urgent earn 5000 daily apply"
```

---

## 3. Feature Extraction

JobGuard uses **TF-IDF (Term Frequency–Inverse Document Frequency)**.

Both:

```text
Unigrams
```

and:

```text
Bigrams
```

are used.

For example:

```text
registration
registration fee
bank
bank account
no interview
guaranteed income
```

can become important features.

---

## 4. Classification

The project uses:

```text
Logistic Regression
```

with:

```text
class_weight = balanced
```

This helps when legitimate and fraudulent job postings are not equally represented.

---

# 📊 Evaluation Metrics

JobGuard evaluates the trained model using:

| Metric | Description |
|---|---|
| Accuracy | Overall percentage of correct predictions |
| Precision | How many predicted scams were actually scams |
| Recall | How many actual scams were detected |
| F1 Score | Balance between precision and recall |
| ROC AUC | Ability of the model to distinguish classes |

For scam detection, **precision and recall are especially important**, since both false alarms and missed scams matter.

---

# 🚨 Scam Risk Classification

The probability generated by the model is converted into an easy-to-understand risk level.

| Probability | Risk |
|---:|---|
| 0–40% | 🟢 Low |
| 40–60% | 🟡 Medium |
| 60–80% | 🟠 High |
| 80–100% | 🔴 Very High |

The final ML classification is:

```text
🟢 LIKELY LEGITIMATE
```

or

```text
🚨 POTENTIAL JOB SCAM
```

---

# 🛠️ Tech Stack

### Programming Language

- Python

### Machine Learning

- Scikit-learn
- Logistic Regression

### Natural Language Processing

- TF-IDF
- Text preprocessing
- N-grams

### Data Processing

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn
- Plotly

### User Interface

- Gradio

### Development Environment

- Google Colab

---

# 📁 Project Structure

The project can be organized as:

```text
JobGuard/
│
├── JobGuard.ipynb
│
├── README.md
│
├── data/
│   └── fake_job_postings.csv
│
├── results/
│   ├── confusion_matrix.png
│   └── predictions.csv
│
├── requirements.txt
│
└── LICENSE
```

Since the current implementation is designed as a **single Google Colab cell**, the complete application can also simply be maintained as:

```text
JobGuard/
│
├── JobGuard.ipynb
└── README.md
```

---

# 🚀 Running the Project

## Option 1 — Google Colab

Open the notebook in Google Colab.

Run the complete code cell.

The required packages are automatically installed.

The application will launch with a public Gradio interface.

---

## Option 2 — Local Environment

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/JobGuard.git
cd JobGuard
```

Install dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly gradio openpyxl
```

Then launch the notebook using:

```bash
jupyter notebook
```

---

# 📂 Dataset Format

A training dataset should contain a target column indicating whether a job posting is fraudulent.

For example:

```csv
title,company_profile,description,location,employment_type,fraudulent
Software Engineer,ABC Technologies,Develop software applications,India,Full-time,0
Work From Home,Unknown Company,Pay a registration fee to start,Worldwide,Remote,1
```

Where:

```text
0 = Legitimate
1 = Fraudulent
```

The implementation also recognizes common alternative labels such as:

```text
fraud
scam
fake
target
label
```

---

# 🧪 Example Prediction

### Input

```text
Job Title:
Work From Home Data Entry

Company:
Online Careers

Description:
Earn $5000 every week with no experience.
No interview required.
Pay a registration fee of $100.
Send your bank details and OTP to our recruiter.
```

### JobGuard Output

```text
🚨 POTENTIAL JOB SCAM

Risk Level:
🔴 VERY HIGH RISK

Scam Probability:
94.31%
```

### Detected Indicators

```text
no experience
no interview
registration fee
bank details
OTP
guaranteed income
```

---

# 🔐 Safety Considerations

JobGuard should be treated as a **screening and decision-support system**, not as an absolute fraud detector.

A high probability does not mathematically prove that a job is fraudulent.

Likewise, a low probability does not guarantee that a job is safe.

Users should independently verify:

- Official company website
- Official careers page
- Recruiter email domain
- Company LinkedIn profile
- Interview process
- Salary claims
- Employment contract
- Requests for money
- Requests for OTPs
- Requests for passwords
- Requests for banking credentials

**Never send an OTP, password, or banking credentials to a recruiter.**

---

# 🔮 Future Improvements

The current system uses TF-IDF + Logistic Regression. It can be extended with more advanced NLP and security features.

### 🤖 Advanced NLP

- BERT
- RoBERTa
- DistilBERT
- Sentence Transformers
- Transformer-based classification

### 🔍 Explainable AI

- SHAP
- LIME
- Word-level explanations
- Feature contribution visualization

### 🌐 Web Application

Build a full production application using:

```text
React
    ↓
FastAPI / Flask
    ↓
JobGuard ML Model
    ↓
PostgreSQL / MySQL
```

### 🔎 Additional Scam Detection

Add detection for:

- Suspicious URLs
- Domain reputation
- Email-domain verification
- Company verification
- Salary anomaly detection
- Duplicate job postings
- Recruiter behavior
- Phone-number patterns
- Cryptocurrency payment requests

### 📡 Real-Time Detection

A browser extension could automatically analyze job advertisements on supported job platforms.

---

# 💼 Resume Description

You can use the following description on your resume:

> **JobGuard — Fake Job & Scam Detection System:** Developed an NLP-based machine learning system using TF-IDF and Logistic Regression to classify potentially fraudulent job postings. Implemented automated text preprocessing, probability-based risk scoring, suspicious-indicator detection, model evaluation, batch prediction, and an interactive Gradio dashboard for real-time job scam analysis.

---

# 📌 Key Skills Demonstrated

This project demonstrates experience with:

```text
Python
Machine Learning
Natural Language Processing
TF-IDF
Logistic Regression
Scikit-learn
Pandas
NumPy
Data Preprocessing
Feature Engineering
Classification
Model Evaluation
Data Visualization
Plotly
Gradio
Google Colab
CSV/Excel Processing
Explainable ML
```

---

# 🌟 Why JobGuard?

Job scams are increasingly difficult to identify because fraudulent advertisements can look similar to legitimate job postings.

JobGuard attempts to automate the first level of screening by combining:

```text
NLP
  +
Machine Learning
  +
Risk Scoring
  +
Explainability
  +
Interactive UI
```

This makes it a practical machine-learning project rather than simply a model-training experiment.

---

# 📜 License

This project is released under the **MIT License**.

---

# 👨‍💻 Author

**Dheeraj Chilla**

B.Tech — Computer Science & Engineering

Interested in:

- Artificial Intelligence
- Machine Learning
- Data Science
- Full-Stack Development
- NLP
- Software Engineering

---

## ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.

**Built with Python 🐍 + NLP 🧠 + Machine Learning 🤖**
