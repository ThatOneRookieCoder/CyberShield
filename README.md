AI-Based Email Spam & Phishing Detection
📖 Overview

This project implements AI-based detection for email spam and malicious phishing URLs.
It combines machine learning, feature engineering, and unsupervised clustering to detect suspicious content and evaluate models.

Built with Python, scikit-learn, pandas, matplotlib, and seaborn.

⚡ Features
Email Spam Detection

Clean and preprocess email subjects and messages.

TF-IDF vectorization for feature extraction.

Models used:

Logistic Regression

SVM

Naive Bayes

Decision Tree

Gradient Boosting

Random Forest

K-Means clustering for pattern analysis.

Model evaluation:

Accuracy, Precision, Recall, F1-score

Confusion matrix

ROC curve

Save and load models for real-time prediction.

Phishing URL Detection

URL feature extraction (length, dots, hyphens, digits, https, IP presence, suspicious keywords).

Models used:

Logistic Regression

SVM

Naive Bayes

Decision Tree

Gradient Boosting

Random Forest

Model evaluation with ROC curves.

Heuristic checks for:

Suspicious TLDs

Trusted domains

Save and load the best model for real-world URL predictions.

🛠 Requirements

Python 3.8+

Python libraries:

pip install pandas numpy matplotlib seaborn scikit-learn joblib

Datasets:

enron_spam_data.csv – Email spam dataset

malicious_phish.csv – Phishing URL dataset

🚀 Usage
Spam Detection
from joblib import load

model = load("saved_models/spam_logistic.pkl")
vectorizer = load("saved_models/tfidf_vectorizer.pkl")

def predict_email_spam(text):
    text = clean_text(text)
    X_input = vectorizer.transform([text])
    prediction = model.predict(X_input)[0]
    return "Spam" if prediction==1 else "Ham"

# Example
predict_email_spam("URGENT: Your bank account has been suspended.")
predict_email_spam("Hi John, can we schedule the meeting?")
Phishing URL Detection
from joblib import load
from urllib.parse import urlparse

model = load("saved_models/phish_best_model.pkl")

def predict_phishing_url(url):
    # Apply heuristic and ML model prediction
    ...
    return "Phishing" or "Legitimate"

# Example
predict_phishing_url("http://secure-login-paypal-update-account.ru")
predict_phishing_url("https://www.google.com")
📂 Project Structure
.
├── enron_spam_data.csv
├── malicious_phish.csv
├── saved_models/
│   ├── spam_logistic.pkl
│   ├── tfidf_vectorizer.pkl
│   └── phish_best_model.pkl
├── spam_phishing_detection.ipynb
└── README.md
📊 Model Evaluation

Metrics: Accuracy, Precision, Recall, F1-score

Visualizations:

Confusion Matrix

ROC Curve Comparison

K-Means clustering for spam patterns.

🔗 References

Enron Email Dataset

scikit-learn documentation

Python official documentation
