# 🛡️ Flask Sentiment Analyzer with Rate Limiting

A simple AI-powered sentiment analysis web app built with Flask that demonstrates both **machine learning integration** and **web application defense**.  

This project showcases how a basic Flask app can be secured against denial-of-service (DoS) style floods using a rate limiter, while also delivering a functional Natural Language Processing (NLP) service.

---

## 🚀 Features

- **Sentiment Analysis**
  - Uses Hugging Face's model.
  - Classifies text as **Positive** or **Negative** with a confidence score.

- **Flask Web Application**
  - Lightweight, easy-to-deploy Python web framework.
  - Clean HTML form for user input.

- **Security Defense**
  - Integrated `Flask-Limiter` to prevent brute-force and DoS attempts.
  - Requests are capped at `5 per minute` per IP.
  - Resistant to flooding tools like Slowloris.

---

## 🖼️ Demo Screenshots


1. **Homepage** – Your Flask app form with the input box visible.  
2. **Positive Sentiment Result** – Example: “I love this project!” → **Positive**.  
3. **Negative Sentiment Result** – Example: “This is terrible.” → **Negative**.  
4. **429 Too Many Requests** – After triggering the rate limiter.  
5. **Terminal Logs** – Showing Slowloris attack attempts alongside Flask app staying alive.  

---

## ⚔️ Attack vs Defense

### Without Rate Limiting
- Flooding the app with Slowloris quickly overwhelms the Flask server.
- Normal users can no longer access the service.

### With Rate Limiting
- The limiter restricts abusive requests (returns `429 Too Many Requests`).
- The app remains responsive for legitimate users.
- Demonstrates how a simple defense layer drastically increases resilience.

---

## ⚙️ Installation

Clone the repo and set up a virtual environment:

git clone https://github.com/Ayo223556762/flask-sentiment-analyzer.git
cd flask-sentiment-analyzer
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
Run the app:

bash
Copy
Edit
python3 app.py
Then open in browser:

cpp
Copy
Edit
http://127.0.0.1:5000
## 📚 Tech Stack
Flask – Python web framework

Hugging Face Transformers – NLP model

Flask-Limiter – Rate limiting & DoS defense

Slowloris – DoS simulation tool (for lab only)

## 🏆 Learning Outcomes
Integrated an AI model into a live Flask web app.

Performed an offensive DoS simulation against the app.

Applied defensive rate limiting to keep the app resilient.

Documented the process to show practical DevSecOps skills.





