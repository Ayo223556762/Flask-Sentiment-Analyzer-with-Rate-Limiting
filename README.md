# 🛡️ Flask Sentiment Analyzer with Rate Limiting

A simple AI-powered sentiment analysis web app built with Flask that demonstrates both **machine learning integration** and **web application defense**.  

This project shows how a Flask app can be **attacked with a DoS flood** and then secured using a **rate limiter** to stay resilient.

---

## 🚀 Features

- **Sentiment Analysis**
  - Uses Hugging Face's `distilbert-base-uncased-finetuned-sst-2-english` model.
  - Classifies text as **Positive** or **Negative** with a confidence score.

- **Flask Web Application**
  - Lightweight Python web framework.
  - Simple text form for analysis.

- **Security Defense**
  - Integrated `Flask-Limiter` to prevent brute-force and DoS attacks.
  - Requests capped at `5 per minute` per IP.
  - Tested successfully against a Slowloris flood.

---

## 🖼️ Demo Screenshots

Add these screenshots in a `screenshots/` folder:
- Homepage form
- 429 Too Many Requests (rate limiter triggered)  
- Terminal showing Slowloris attack with app still alive  

⚔️ Attack vs Defense
Without Rate Limiting
DoS flood with Slowloris overwhelms Flask instantly.

Normal users cannot access the service.

With Rate Limiting
App returns 429 Too Many Requests after the limit.

Legit users remain unaffected.

Demonstrates why production apps need defenses.

## 🛠️ Step-by-Step Setup
1. Clone the Repo
git clone https://github.com/Ayo223556762/flask-sentiment-analyzer.git
cd flask-sentiment-analyzer

2. Create and Activate a Virtual Environment
python3 -m venv venv
source venv/bin/activate

3. Install Dependencies
pip install flask flask-limiter transformers torch

4. Run the App
python3 app.py

App will start at:http://127.0.0.1:5000

## 🔑 Rate Limiter Code
from flask_limiter import Limiter
from flask_limiter.util import get_remote_address

limiter = Limiter(
    get_remote_address,
    app=app,
    default_limits=["10 per minute"]
)

@app.route("/", methods=["GET", "POST"])
@limiter.limit("5 per minute")
def home():
    ...
⚡ DoS Simulation with Slowloris
Run Flask app first, then in a new terminal:
slowloris 127.0.0.1 -p 5000 -s 200 -v
Without limiter → Flask freezes.
With limiter → returns 429 and stays online.

📚 Tech Stack
Flask – Python web framework

Hugging Face Transformers – NLP model

Flask-Limiter – DoS protection

Slowloris – DoS simulation

🏆 Learning Outcomes
Built a working AI web app in Flask.

Performed an offensive DoS simulation.

Secured the app with a rate limiter.

Documented a full red‑team and defense lab.
