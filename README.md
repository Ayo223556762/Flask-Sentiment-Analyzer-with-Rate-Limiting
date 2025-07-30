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

Include these screenshots for maximum impact:

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

```bash
git clone https://github.com/YOURUSERNAME/flask-sentiment-analyzer.git
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
📚 Tech Stack
Flask – Python web framework

Hugging Face Transformers – NLP model

Flask-Limiter – Rate limiting & DoS defense

Slowloris – DoS simulation tool (for lab only)

🏆 Learning Outcomes
Integrated an AI model into a live Flask web app.

Performed an offensive DoS simulation against the app.

Applied defensive rate limiting to keep the app resilient.

Documented the process to show practical DevSecOps skills.

👨‍💻 Author
Ayo Adejumo
Master’s Student in Cybersecurity | Red Team & DevSecOps Enthusiast

yaml
Copy
Edit

---

⚡ **Action Items for You:**
- Grab the **5 screenshots** I listed above.  
- Save them into a folder called `screenshots/` in your repo.  
- Update the README with image links, like:
```markdown
![Homepage](screenshots/homepage.png)
![Rate Limit Trigger](screenshots/429.png)
Do you want me to also whip up a requirements.txt for you, so anyone cloning your repo can pip install -r requirements.txt without guessing dependencies?







You said:
read me looks good but i need the step-by-step included in there like the code and cmd i typed, Ayo223556762 is my githubname, fill it in 


ChatGPT said:
Bet ✅ — we’ll keep it clean and professional but also show off the exact step‑by‑step you ran so anyone (or a recruiter) can reproduce it. That makes your repo way more legit. I’ll drop in your GitHub username too.

Here’s your final polished README.md:

markdown
Copy
Edit
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
- Positive sentiment result  
- Negative sentiment result  
- 429 Too Many Requests (rate limiter triggered)  
- Terminal showing Slowloris attack with app still alive  

Example:
```markdown
![Homepage](screenshots/homepage.png)
![Rate Limit Trigger](screenshots/429.png)
⚔️ Attack vs Defense
Without Rate Limiting
DoS flood with Slowloris overwhelms Flask instantly.

Normal users cannot access the service.

With Rate Limiting
App returns 429 Too Many Requests after the limit.

Legit users remain unaffected.

Demonstrates why production apps need defenses.

🛠️ Step-by-Step Setup
1. Clone the Repo
bash
Copy
Edit
git clone https://github.com/Ayo223556762/flask-sentiment-analyzer.git
cd flask-sentiment-analyzer
2. Create and Activate a Virtual Environment
bash
Copy
Edit
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
bash
Copy
Edit
pip install flask flask-limiter transformers torch
4. Run the App
bash
Copy
Edit
python3 app.py
App will start at:

cpp
Copy
Edit
http://127.0.0.1:5000
🔑 Rate Limiter Code
python
Copy
Edit
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

bash
Copy
Edit
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

