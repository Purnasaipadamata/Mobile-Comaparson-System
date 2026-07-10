# 📱 AI-Based Mobile Comparison System

An intelligent web application that helps users compare smartphones using **AI-driven recommendations**, **spec-based analysis**, and **sentiment-based review scoring** — making phone buying decisions faster, smarter, and data-backed.

![Status](https://img.shields.io/badge/status-active-success)
![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/python-3.10%2B-yellow)
![Made with](https://img.shields.io/badge/made%20with-Flask%20%7C%20React%20%7C%20ML-orange)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How It Works](#-how-it-works)
- [Installation](#-installation)
- [Usage](#-usage)
- [Dataset](#-dataset)
- [Machine Learning Model](#-machine-learning-model)
- [API Reference](#-api-reference)
- [Screenshots](#-screenshots)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## 🧠 Overview

The **AI-Based Mobile Comparison System** is designed to eliminate confusion when choosing between multiple smartphone models. Instead of manually comparing specs across dozens of tabs, users can:

- Select two or more phones and instantly get a **side-by-side comparison**
- Receive an **AI-generated recommendation** based on their usage priorities (camera, gaming, battery, budget, etc.)
- View a **sentiment score** derived from real user reviews, scraped and analyzed using NLP
- Get a **value-for-money score** computed from a weighted ML model

This project blends **traditional spec comparison** with **machine learning** to produce recommendations that go beyond simple number-matching.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔍 **Smart Search** | Autocomplete-based search across a large mobile phone database |
| ⚖️ **Multi-Phone Comparison** | Compare 2–4 phones side-by-side on specs, price, and performance |
| 🤖 **AI Recommendation Engine** | Suggests the "best fit" phone based on user-defined priorities (weights) |
| 💬 **Review Sentiment Analysis** | NLP model scores real user reviews as positive/neutral/negative |
| 📊 **Value Score** | ML-based score combining price, specs, and sentiment into one metric |
| 📈 **Price Trend Insights** | Historical price tracking and drop predictions |
| 🌐 **Responsive UI** | Fully responsive comparison dashboard for mobile and desktop |
| 🔐 **User Accounts** | Save comparisons, wishlists, and get personalized suggestions |

---

## 🏗️ System Architecture

```
┌─────────────┐        ┌──────────────┐        ┌────────────────┐
│   Frontend   │  <-->  │  Backend API  │  <-->  │   ML Service    │
│ (React.js)   │        │ (Flask/Django)│        │ (Recommendation │
│              │        │               │        │  + Sentiment)   │
└─────────────┘        └──────┬───────┘        └────────────────┘
                               │
                               ▼
                     ┌───────────────────┐
                     │   Database (SQL /  │
                     │   MongoDB)         │
                     │  Phones, Reviews,  │
                     │  Users, Prices     │
                     └───────────────────┘
```

**Flow:**
1. User selects phones to compare via the frontend.
2. Backend fetches specs, prices, and reviews from the database.
3. ML service computes sentiment scores and a weighted recommendation score.
4. Results are returned and rendered as an interactive comparison table + AI verdict.

---

## 🛠️ Tech Stack

**Frontend:**
- React.js / Next.js
- Tailwind CSS
- Chart.js / Recharts (for visual comparisons)

**Backend:**
- Python (Flask or Django REST Framework)
- Node.js (optional API gateway)

**Machine Learning / NLP:**
- Scikit-learn (recommendation scoring model)
- NLTK / spaCy / Transformers (sentiment analysis on reviews)
- Pandas, NumPy (data processing)

**Database:**
- MongoDB / PostgreSQL / MySQL

**Others:**
- Docker (containerization)
- BeautifulSoup / Scrapy (review & spec scraping, if applicable)
- JWT (authentication)

---

## 📁 Project Structure

```
ai-mobile-comparison-system/
│
├── frontend/                  # React/Next.js client
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── utils/
│   └── package.json
│
├── backend/                   # Flask/Django API
│   ├── app/
│   │   ├── routes/
│   │   ├── models/
│   │   └── services/
│   ├── requirements.txt
│   └── run.py
│
├── ml_engine/                 # ML & NLP models
│   ├── recommendation_model.py
│   ├── sentiment_analysis.py
│   ├── train_model.ipynb
│   └── model_weights/
│
├── data/                      # Datasets
│   ├── phones.csv
│   └── reviews.csv
│
├── docs/                      # Documentation & diagrams
│
├── .env.example
├── docker-compose.yml
└── README.md
```

---

## ⚙️ How It Works

1. **Data Collection** — Phone specifications and user reviews are collected/scraped and stored in the database.
2. **Preprocessing** — Specs are normalized (e.g., RAM, battery, camera MP) and reviews are cleaned for NLP processing.
3. **Sentiment Analysis** — Each review is classified as positive, neutral, or negative using a trained NLP model, producing an aggregate sentiment score per phone.
4. **Recommendation Scoring** — A weighted scoring model combines:
   - Normalized spec scores (camera, battery, performance, display)
   - Price-to-spec ratio
   - Review sentiment score
   - User-defined priority weights (e.g., "I care more about camera than battery")
5. **Result Generation** — The system outputs a ranked comparison with an AI-generated verdict, e.g., *"Phone A is the better choice for photography and battery life, while Phone B offers better value for gaming."*

---

## 💻 Installation

### Prerequisites
- Python 3.10+
- Node.js 18+
- MongoDB or PostgreSQL installed locally (or use Docker)

### Clone the repository
```bash
git clone https://github.com/your-username/ai-mobile-comparison-system.git
cd ai-mobile-comparison-system
```

### Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env          # configure DB & API keys
python run.py
```

### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

### ML Engine Setup
```bash
cd ml_engine
pip install -r requirements.txt
python train_model.py         # trains/loads the recommendation & sentiment models
```

### Run with Docker (optional, all-in-one)
```bash
docker-compose up --build
```

The app will be available at `http://localhost:3000` (frontend) and `http://localhost:5000` (API).

---

## 🚀 Usage

1. Open the app and search for a phone (e.g., "iPhone 15", "Galaxy S24").
2. Add 2–4 phones to the comparison tray.
3. Set your priorities using the sliders (Camera, Battery, Performance, Price, Display).
4. Click **Compare Now**.
5. View the side-by-side spec table, sentiment scores, and the AI's final recommendation with reasoning.

---

## 🗂️ Dataset

The system uses a structured dataset containing:

| Field | Description |
|---|---|
| `phone_id` | Unique identifier |
| `brand`, `model` | Phone identity |
| `price` | Current market price |
| `ram`, `storage`, `battery_mah` | Core specs |
| `camera_mp`, `display_size`, `refresh_rate` | Feature specs |
| `processor` | Chipset details |
| `release_date` | Launch date |
| `reviews` | Linked user review text and ratings |

> You can plug in your own dataset (CSV/JSON) or connect a live scraper — see `ml_engine/train_model.ipynb` for the expected schema.

---

## 🤖 Machine Learning Model

- **Recommendation Model**: A weighted scoring algorithm (extendable to a trained regression/ranking model) that normalizes specs and combines them with user-defined weights to output a 0–100 "Fit Score" per phone.
- **Sentiment Model**: A text classification model (fine-tuned Transformer or a classical TF-IDF + Logistic Regression baseline) that scores reviews as positive/neutral/negative and aggregates them into a per-phone sentiment index.
- **Evaluation**: Model performance is tracked using accuracy/F1 for sentiment classification, and correlation with actual user purchase satisfaction ratings for the recommendation engine.

---

## 🔌 API Reference

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/phones` | Fetch all phones (supports filters & search) |
| `GET` | `/api/phones/:id` | Get details of a single phone |
| `POST` | `/api/compare` | Compare a list of phone IDs, returns spec + sentiment + score |
| `POST` | `/api/recommend` | Get AI recommendation based on user priority weights |
| `GET` | `/api/reviews/:phone_id` | Fetch reviews and sentiment breakdown for a phone |
| `POST` | `/api/auth/login` | User login |
| `POST` | `/api/auth/register` | User registration |

**Example Request — `/api/compare`**
```json
{
  "phone_ids": ["p101", "p102"],
  "priorities": {
    "camera": 0.4,
    "battery": 0.3,
    "performance": 0.2,
    "price": 0.1
  }
}
```

**Example Response**
```json
{
  "winner": "p101",
  "scores": {
    "p101": 87.5,
    "p102": 81.2
  },
  "reasoning": "Phone p101 scores higher due to superior camera performance and stronger sentiment from user reviews."
}
```

---

## 🖼️ Screenshots

> _Add screenshots or GIFs of your app here to showcase the UI._

| Home / Search | Comparison View | AI Recommendation |
|---|---|---|
| ![home](docs/screenshots/home.png) | ![compare](docs/screenshots/compare.png) | ![recommend](docs/screenshots/recommend.png) |

---

## 🗺️ Roadmap

- [ ] Add voice-based search ("Find me a phone under 20k with good camera")
- [ ] Integrate live price tracking from e-commerce APIs
- [ ] Add chatbot assistant for conversational recommendations
- [ ] Multi-language support for reviews (Hindi, Telugu, etc.)
- [ ] Mobile app version (React Native / Flutter)

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please make sure to update tests and documentation as appropriate.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 📬 Contact

**Project Maintainer:** Your Name
📧 Email: your.email@example.com
🔗 LinkedIn: [LinkedIn Profile](https://www.linkedin.com/in/purna-sai-padamata-9012732a0)
🐙 GitHub: [@GitHub](https://github.com/Purnasaipadamata/)

---

⭐ If you find this project useful, consider giving it a star on GitHub — it helps a lot!
