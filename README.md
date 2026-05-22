# 🩸 RaktSetu — Your Bridge to Saving Lives

**Live Demo:** https://raktsetu-74u1.onrender.com

An AI-powered blood donation assistant chatbot built for Bangalore. RaktSetu helps users check donation eligibility, find nearby blood banks, understand blood group compatibility, and handle emergency blood requests — all through a clean, conversational interface.

Built with Flask and Google Gemini API for AAT2: Social Impact Chatbot Development.

---

## Features

- **AI-Powered Chat** — Natural conversations powered by Google Gemini 2.5 Flash with a domain-specific knowledge base
- **Eligibility Checker** — Determines if a user can donate blood based on NACO/NBTC guidelines
- **Blood Bank Finder** — 15 real Bangalore blood banks with phone numbers and location-based suggestions
- **Blood Group Compatibility** — Complete donor-recipient compatibility information
- **Emergency Mode** — One-tap emergency button for urgent blood requests
- **Interactive Map** — Leaflet.js map with markers for all blood banks in Bangalore
- **Bilingual Support** — Toggle between English and Kannada (ಕನ್ನಡ)
- **Location Awareness** — Select your area in Bangalore for nearby blood bank recommendations
- **Awareness Modal** — Embedded WHO video on blood donation importance
- **Conversation Memory** — Full chat history maintained across the session

---

## Project Structure

```
raktsetu/
├── app.py                  # Flask backend — routes, Gemini API calls, system prompt
├── .env                    # Environment variables (API key — not in repo)
├── .gitignore              # Files excluded from git
├── requirements.txt        # Python dependencies
├── Procfile                # Deployment config for Render/Railway
├── README.md               # This file
└── templates/
    ├── index.html          # Main chat interface (HTML + CSS + JS)
    └── map.html            # Blood bank map page with Leaflet.js
```

---

## Tech Stack

| Layer      | Technology                  |
|------------|-----------------------------|
| Backend    | Python, Flask               |
| AI Model   | Google Gemini 2.5 Flash     |
| Frontend   | HTML, CSS, Vanilla JS       |
| Map        | Leaflet.js (OpenStreetMap)  |
| Deployment | Render / Railway            |

---

## Run Locally

### Prerequisites

- Python 3.10+
- A Google Gemini API key ([get one here](https://aistudio.google.com))

### Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/yourusername/raktsetu.git
   cd raktsetu
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate        # Mac/Linux
   venv\Scripts\activate           # Windows
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Add your API key**

   Create a `.env` file in the project root:
   ```
   GEMINI_API_KEY=your_api_key_here
   ```

5. **Run the app**
   ```bash
   python app.py
   ```

6. **Open in browser**
   ```
   http://localhost:5002
   ```

---

## How It Works

1. User sends a message through the chat interface
2. Frontend sends the message + full conversation history to `/chat` (POST)
3. Flask backend constructs the prompt: system instruction + history + new message
4. Gemini API processes the prompt and returns a response
5. Backend sends the response back as JSON
6. Frontend displays it in the chat and stores it in the history array
7. The cycle repeats — full history is sent every time to maintain context

---

## System Prompt

The chatbot's knowledge base is embedded in a detailed system prompt that includes:

- Personality and tone guidelines (calm, reassuring, no markdown)
- Complete blood donation eligibility criteria per NACO/NBTC
- Blood group compatibility chart
- 15 Bangalore blood banks with addresses and phone numbers
- Emergency handling procedures
- Donation process walkthrough
- Common myth corrections
- Off-topic rejection instructions

---

## API Endpoints

| Method | Route   | Description                        |
|--------|---------|------------------------------------|
| GET    | `/`     | Serves the main chat interface     |
| POST   | `/chat` | Receives message + history, returns AI response |
| GET    | `/map`  | Serves the blood bank map page     |

---

## Deployment

Deployed on Render (free tier):

1. Push to GitHub
2. Connect repo on [render.com](https://render.com)
3. Set build command: `pip install -r requirements.txt`
4. Set start command: `gunicorn app:app`
5. Add environment variable: `GEMINI_API_KEY`
6. Deploy

---

## Team

Built by **Sumedh** and **Sujay**

---

## License

This project was built for academic purposes (AAT2 submission). Feel free to fork and adapt for your own use.
