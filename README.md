# CyberShield – AI-Based Spam & Phishing Detection

## Project Overview
**CyberShield** is a Python-based machine learning project for detecting:

1. **Spam emails/messages** – using email subject + message content.  
2. **Phishing URLs** – analyzing URL structure and suspicious patterns.

It combines **supervised learning** (Logistic Regression, Random Forest, SVM, Naive Bayes, Decision Tree, Gradient Boosting) with **unsupervised learning** (K-Means clustering) for pattern analysis.  

**Intended Users:** Email users, organizations, and cybersecurity professionals.

---

## Environment Setup

### Prerequisites
- Python 3.10+  
- Terminal or command prompt  
- Recommended: virtual environment (venv)  

### Create & Activate Virtual Environment
```bash
cd path/to/CyberShield
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
Install Dependencies
pip install pandas numpy scikit-learn matplotlib seaborn joblib
Project Structure
/CyberShield
│
├─ /data                 # Raw & processed datasets (CSV/JSON)
├─ /saved_models         # Saved ML models (.pkl)
├─ Assignment2.ipynb       # Main notebook
├─ preprocess.py         # Optional preprocessing script
├─ train_models.py       # Optional training script
├─ evaluate_models.py    # Optional evaluation script
├─ predict_spam.py       # Spam prediction script
├─ predict_phish.py      # Phishing prediction script
└─ README.md             # This file
Datasets
Spam Dataset

File: enron_spam_data.csv

Columns: Subject, Message, Spam/Ham

Labels: spam = 1, ham = 0

Preprocessing: Clean text, lowercase, concatenate subject + message

Phishing Dataset

File: malicious_phish.csv

Columns: url, type (benign/malicious)

Labels: malicious = 1, benign = 0

Feature Engineering: URL length, dots, hyphens, digits, HTTPS, suspicious words, IP detection, domain analysis

Running the Project
1. Preprocessing & Feature Extraction
python preprocess.py

Cleans email text

Generates TF-IDF features for spam

Extracts URL-based features for phishing

2. Train Models
python train_models.py

Trains spam detection models: Logistic Regression, SVM, Naive Bayes, Decision Tree, Gradient Boosting

Trains phishing detection models: Logistic Regression, SVM, Naive Bayes, Decision Tree, Gradient Boosting, Random Forest

Saves trained models to /saved_models/

3. Evaluate Models
python evaluate_models.py

Computes Accuracy, Precision, Recall, F1

Generates confusion matrices and ROC curves

Unsupervised Pattern Analysis

Uses Truncated SVD + K-Means to cluster spam/ham emails.

Compare clusters with actual labels to analyze patterns.

Visualized with 2D scatter plots.

Real-World Predictions
Spam Email
from predict_spam import predict_email_spam

predict_email_spam("URGENT: Your bank account has been suspended. Click here to verify your account immediately.")
predict_email_spam("Hi John, can we schedule the meeting for tomorrow morning?")

Output: "Spam" or "Ham"

Phishing URL
from predict_phish import predict_phishing_url

predict_phishing_url("http://secure-login-paypal-update-account.ru")
predict_phishing_url("https://www.google.com")

Output: "Phishing" or "Legitimate"

Key Features

Spam Detection: TF-IDF vectorization, supervised ML models

Phishing Detection: URL feature extraction, classification models

Pattern Analysis: K-Means clustering on email dataset

Evaluation: Confusion matrix, ROC curves, Accuracy, Precision, Recall, F1

Saved Models: .pkl files for prediction

How to Use

Place datasets in /data

Run preprocessing to clean and extract features

Train models to generate .pkl files

Evaluate models and visualize performance

Make predictions using predict_email_spam() or predict_phishing_url()

References

Apache SpamAssassin Public Corpus – https://spamassassin.apache.org/old/publiccorpus/

scikit-learn Documentation – https://scikit-learn.org/

pandas Documentation – https://pandas.pydata.org/

matplotlib Documentation – https://matplotlib.org/
