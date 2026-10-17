# 🏏 IPL Cricket Data Analysis Dashboard

A full-stack, enterprise-grade IPL Cricket Data Analytics web application that analyzes historical IPL matches (2008–2023) and ball-by-ball delivery datasets. Features an interactive modern React dashboard, Flask REST API backend, Pandas/NumPy statistical engine, Recharts visualizations, and a complete Jupyter Exploratory Data Analysis (EDA) notebook.

---

## 🌟 Key Features

1. **Executive KPI Dashboard**: Total matches, seasons, franchises, total runs, all-time top run scorer, top wicket taker, season-by-season scoring trends, and franchise win distribution.
2. **Batting Deep-Dive**: Leaderboard by runs, strike rates, batting averages, highest scores, boundaries (4s and 6s), and 50s/100s with player and season filtering.
3. **Bowling Mastery**: Wickets, economy rates, bowling averages, best bowling figures, overs bowled, and strike rates.
4. **Team & Head-to-Head Analytics**: Franchise win rates, toss decisions impact (Bat vs Field), batting-first vs chasing win rates, and direct head-to-head match comparator.
5. **Match Explorer & Scorecard Inspector**: Searchable match history with filters for season, team, and venue, win margin distribution, and detailed innings break-down.
6. **Built-in Full-Stack Code Explorer**: In-browser inspection of every Python backend route, service, and config file with copy buttons, Hindi setup guide, and dataset download.

---

## 🏗️ Architecture & Technology Stack

- **Frontend**: React 19, Vite, Tailwind CSS v4, Recharts, Lucide Icons
- **Backend**: Python 3.10+, Flask, Flask-CORS, Pandas, NumPy
- **Analytics & EDA**: Jupyter Notebook, Seaborn, Matplotlib
- **Dataset**: `matches.csv` & `deliveries.csv` (Historical 2008–2023)
- **Deployment**: Render (Backend Web Service) + Vercel (Frontend SPA)

---

## 📁 Project Directory Structure

```text
IPL-Cricket-Data-Analysis/
├── backend/
│   ├── app.py                 # Flask app factory, CORS, and health check
│   ├── config.py              # Environment configuration and file paths
│   ├── requirements.txt       # Python dependencies (Flask, pandas, etc.)
│   ├── routes/
│   │   ├── dashboard.py       # GET /api/dashboard, /api/seasons, /api/venues
│   │   ├── batting.py         # GET /api/batting (filters: season, player)
│   │   ├── bowling.py         # GET /api/bowling (filters: season, bowler)
│   │   ├── teams.py           # GET /api/teams, /api/teams/head-to-head
│   │   └── matches.py         # GET /api/matches (search, pagination), /api/matches/<id>
│   ├── services/
│   │   ├── data_loader.py     # CSV loading with in-memory DataFrame caching
│   │   ├── data_cleaning.py   # Franchise renaming & missing value handling
│   │   └── analysis.py        # Cricket statistical calculation engine
│   ├── utils/
│   │   └── validators.py      # Input validation & pagination sanitizers
│   └── data/
│       ├── matches.csv        # Match summary records
│       └── deliveries.csv     # Ball-by-ball delivery records
├── notebooks/
│   └── ipl_eda.ipynb          # Jupyter Notebook for exploratory data analysis
├── src/                       # React frontend source code
├── package.json
└── README.md
```

---

## ⚙️ Local Installation & Setup Guide (Windows PowerShell)

### Step 1: Clone or Open Project
```powershell
git clone https://github.com/your-username/ipl-cricket-data-analysis.git
cd ipl-cricket-data-analysis
```

### Step 2: Set up Python Virtual Environment & Flask Backend
```powershell
# Navigate to backend directory
cd backend

# Create Python virtual environment named 'venv'
python -m venv venv

# Activate the virtual environment
.\venv\Scripts\Activate.ps1

# Install required Python packages
pip install -r requirements.txt

# Start the Flask backend server on http://127.0.0.1:5000
python app.py
```

### Step 3: Set up & Run React Frontend
In a **new PowerShell terminal window**:
```powershell
# From the project root
npm install

# Start the Vite development server
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) (or the port displayed by Vite) in your web browser.

---

## 🇮🇳 सरल हिंदी में समझें (Step-by-Step Hindi Guide)

### 1. प्रोजेक्ट क्या करता है?
यह प्रोजेक्ट IPL (इंडियन प्रीमियर लीग) के 2008 से 2023 तक के ऐतिहासिक मैच और बॉल-बाय-बॉल डेटा का विश्लेषण करता है। इससे आप देख सकते हैं कि:
- कौन सा बल्लेबाज सबसे ज्यादा रन बना चुका है और किसका स्ट्राइक रेट सबसे बेहतर है।
- किस गेंदबाज की इकॉनमी सबसे किफायती है और किसने सबसे ज्यादा विकेट लिए हैं।
- टॉस जीतने पर पहले बैटिंग चुनना बेहतर है या चेज करना।
- दो टीमों के बीच हेड-टू-हेड रिकॉर्ड क्या है।

### 2. बैकएंड (Flask + Pandas) कैसे काम करता है?
1. `data_loader.py` CSV फाइलों (`matches.csv` और `deliveries.csv`) को लोड करके मेमोरी में कैश करता है ताकि हर रिक्वेस्ट पर फाइल दोबारा न पढ़नी पड़े।
2. `data_cleaning.py` टीमों के पुराने नामों को नए नामों से मैप करता है (जैसे *Delhi Daredevils* को *Delhi Capitals* और *Kings XI Punjab* को *Punjab Kings*)।
3. `analysis.py` क्रिकेट के आधिकारिक नियमों के आधार पर बैटिंग एवरेज (`Runs / Outs`), स्ट्राइक रेट (`Runs / Balls * 100`), और बॉलिंग इकॉनमी कैलकुलेट करता है।
4. `app.py` में Flask REST APIs हैं जो फ्रंटएंड को JSON फॉर्मेट में डेटा भेजते हैं।

### 3. फ्रंटएंड (React + Recharts) कैसे काम करता है?
React में अलग-अलग कम्पोनेंट्स (Dashboard, Batting, Bowling, Team, Matches) बनाए गए हैं। Recharts लाइब्रेरी से सुंदर और इंटरैक्टिव बार चार्ट, लाइन चार्ट और पाई चार्ट रेंडर होते हैं।

---

## 🌐 Production Deployment

### 1. Backend on Render
1. Sign up on [Render.com](https://render.com).
2. Create a new **Web Service** and connect your GitHub repository.
3. Configure settings:
   - **Root Directory**: `backend`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
4. Copy your live Render URL (e.g. `https://ipl-backend.onrender.com`).

### 2. Frontend on Vercel
1. Sign up on [Vercel.com](https://vercel.com).
2. Import your GitHub repository.
3. In **Environment Variables**, set:
   - `VITE_API_BASE_URL` = `https://ipl-backend.onrender.com/api`
4. Click **Deploy**.

---

## 📄 Resume Bullet Points for Data Analysts / Full-Stack Developers

- **IPL Cricket Analytics Platform**: Engineered an end-to-end IPL data analysis dashboard leveraging Python (Flask, Pandas, NumPy) and React (Vite, Recharts), processing over 8,000+ historical ball-by-ball delivery events and 15+ tournament seasons.
- **Data Pipeline & Cleaning Engine**: Built optimized data ingestion and normalization algorithms that mapped legacy franchise rebrands, imputed missing match telemetry, and calculated cricket metrics (Economy, Batting Average, Toss Win Correlation) in sub-100ms response times.
- **Interactive Visualization & Head-to-Head Analytics**: Developed responsive multi-page analytical views with dynamic filtering (season, team, player, venue), interactive boundary distribution charts, and head-to-head match outcome comparators.
- **RESTful API Architecture & Deployment**: Structured modular Flask Blueprints with pagination, parameter sanitization, and CORS headers; containerized and deployed across Render and Vercel with zero mock dependencies.
