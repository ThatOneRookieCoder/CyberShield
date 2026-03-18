# CyberShield – Full-Stack AI Spam & Phishing Detection Web App

## Project Overview
**CyberShield** is a full-stack web application designed to detect:

1. **Spam emails/messages** – analyzes email subject and message content using machine learning.  
2. **Phishing URLs** – analyzes URL structures and suspicious patterns using ML and rule-based heuristics.

The project uses a **FastAPI backend** to serve models and handle predictions, and a **React frontend** for a user-friendly dashboard, real-time scanning, and analytics.

**Target Users:** General email users, organizations, and cybersecurity practitioners.

---

## Project Structure

### Backend
```text
/backend
│
├─ /saved_models
│  ├─ spam_logistic.pkl       # Spam detection model (Logistic Regression)
│  ├─ tfidf_vectorizer.pkl    # TF-IDF vectorizer for email text
│  └─ phish_best_model.pkl    # Phishing detection model (Random Forest)
├─ main.py                    # FastAPI backend API
└─ tempCodeRunnerFile.py      # Temporary file, optional
Frontend
/frontend
│
├─ /node_modules               # Node.js dependencies
├─ /public                     # Public assets
└─ /src
   ├─ /components              # Reusable React components
   │  ├─ Charts.js             # Confidence bars, pie charts, history graphs
   │  └─ Sidebar.js            # Sidebar navigation
   └─ /pages
      ├─ Analytics.js          # Analytics dashboard
      ├─ Dashboard.js          # Main dashboard
      └─ History.js            # Scan history page
   ├─ App.js                   # Main app file
   ├─ App.css                  # Styles
   ├─ index.js                 # Entry point
   ├─ index.css                # Global CSS
   ├─ logo.svg                 # App logo
   ├─ reportWebVitals.js       # React performance metrics
   └─ setupTests.js            # React testing setup
Environment Setup
Backend

Navigate to the backend folder:

cd backend

Create and activate a virtual environment:

# Create
python -m venv venv

# Activate
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

Install dependencies:

pip install fastapi uvicorn pandas numpy scikit-learn joblib

Run the FastAPI server:

uvicorn main:app --reload

The backend will be available at http://127.0.0.1:8000.

Frontend

Navigate to the frontend folder:

cd frontend

Install dependencies:

npm install

Start the React app:

npm start

The frontend will run at http://localhost:3000.

Features
Email Spam Detection

Uses Logistic Regression + TF-IDF vectorization.

Accepts raw email text and predicts "Spam" or "Legitimate".

Confidence score included.

URL Phishing Detection

Uses Random Forest ML model + rule-based scoring for suspicious patterns.

Predicts "Phishing" or "Legitimate".

Confidence score combines model + rule-based adjustments.

Frontend Dashboard

Real-time input for emails or URLs.

Confidence bar and safety pie chart visualizations.

Displays recent scan history with timestamps.

Export scan history as CSV.

Backend API

POST /predict-email – Predict email spam.

POST /predict-url – Predict URL phishing.

GET / – Health check (API running message).

GET /health – Simple API health status.

GET /stats – Lists features and models loaded.

Example Usage
Predict Email
const response = await fetch("http://127.0.0.1:8000/predict-email", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ text: "URGENT: Verify your account now!" })
});
const data = await response.json();
console.log(data);
// { prediction: "Spam", confidence: 0.87 }
Predict URL
const response = await fetch("http://127.0.0.1:8000/predict-url", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ url: "http://secure-login-paypal-update-account.ru" })
});
const data = await response.json();
console.log(data);
// { prediction: "Phishing", confidence: 0.92 }
How to Use

Start the backend server.

Start the frontend React app.

Use the dashboard to enter email text or URLs for scanning.

View prediction results, confidence, and history analytics.

Optionally, export scan history to CSV.

Saved Models

spam_logistic.pkl – Logistic Regression spam detection model.

tfidf_vectorizer.pkl – TF-IDF vectorizer for email text preprocessing.

phish_best_model.pkl – Random Forest phishing detection model.

References

scikit-learn Documentation

FastAPI Documentation

React Documentation
