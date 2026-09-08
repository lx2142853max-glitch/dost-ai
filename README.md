# 🤖 Dost AI — Hindi + English + Hinglish Chatbot

Ek high-level AI chatbot jo **हिंदी, English aur Hinglish** — teeno mein natural baat karta hai.
FastAPI backend + zero-dependency chat UI. Free API keys se chalta hai.

---

## ✨ Features
- **Auto language detect** — aap jis bhasha mein likhoge, usi mein jawab
- **3 free AI providers** — Groq → OpenRouter → Gemini (jo key mile, use kar leta hai)
- **Offline fallback** — bina key ke bhi basic baat-cheet chalti hai
- Conversation memory, markdown + code blocks, dark/light theme, mobile-friendly
- Padhai, coding, email/writing, translation, ideas, shayari, gappe — sab kuch

---

## 🔑 Step 1 — Free API key lo (2 minute)

**Groq (recommended — sabse fast, generous free tier)**
1. https://console.groq.com pe jao → Google se sign up
2. **API Keys** → *Create API Key* → copy karo (`gsk_...`)

Alternatives:
- OpenRouter: https://openrouter.ai/keys (free models)
- Google Gemini: https://aistudio.google.com/apikey

---

## 💻 Step 2 — Local pe chalao

```bash
pip install -r requirements.txt
export GROQ_API_KEY="gsk_yahan_apni_key"     # Windows: set GROQ_API_KEY=...
python app.py
```
Browser: **http://localhost:8000**

---

## 🚀 Step 3 — FREE Deploy

### Option A — Render.com (sabse easy, recommended)
1. Is folder ko GitHub repo mein push karo:
   ```bash
   git init && git add . && git commit -m "Dost AI chatbot"
   git branch -M main
   git remote add origin https://github.com/USERNAME/dost-ai.git
   git push -u origin main
   ```
2. https://render.com → sign up with GitHub → **New + → Web Service**
3. Apni repo select karo. Render `render.yaml` khud padh lega. Warna manually:
   - Runtime: **Python 3**
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `uvicorn app:app --host 0.0.0.0 --port $PORT`
   - Instance Type: **Free**
4. **Environment** tab → *Add Environment Variable*
   - Key: `GROQ_API_KEY`  Value: `gsk_...`
5. **Create Web Service** → 2-3 min → live link mil jayega:
   `https://dost-ai.onrender.com`

> ⚠️ Free plan 15 min inactivity ke baad sleep hota hai; pehla request ~40 sec lega. Free hi rehta hai.

### Option B — Hugging Face Spaces (sleep nahi hota)
1. https://huggingface.co/new-space → SDK: **Docker** → Create
2. Saari files upload karo (Dockerfile already included hai)
3. Space **Settings → Variables and secrets → New secret**: `GROQ_API_KEY`
4. Live: `https://huggingface.co/spaces/USERNAME/dost-ai`

### Option C — Railway / Koyeb / Fly.io
Repo connect karo, `Procfile` auto-detect hoga, env var `GROQ_API_KEY` add kar do.

---

## ⚙️ Environment Variables

| Variable | Zaroori? | Default |
|---|---|---|
| `GROQ_API_KEY` | recommended | — |
| `OPENROUTER_API_KEY` | optional | — |
| `GEMINI_API_KEY` | optional | — |
| `GROQ_MODEL` | no | `llama-3.3-70b-versatile` |
| `BOT_NAME` | no | `Dost AI` |
| `PORT` | no | `8000` |

---

## 🎨 Customize
- **Personality / rules** → `app.py` mein `SYSTEM_PROMPT` badlo
- **Colors** → `static/index.html` ke `:root` variables
- **Suggestion chips** → `index.html` mein `SUGG` array
- **Naam** → env var `BOT_NAME` + `index.html` ka title

## 🩺 Health check
`GET /api/health` — batata hai kaun si key active hai.

## 📂 Files
```
app.py            FastAPI server + AI logic + offline brain
static/index.html Chat UI (single file)
requirements.txt  Python deps
render.yaml       Render blueprint
Procfile          Railway/Heroku-style deploy
Dockerfile        HF Spaces / any Docker host
.env.example      Key template
```
