# 🚀 Nexa AI

Nexa AI is a high-performance, fullstack AI assistant featuring real-time voice interaction and advanced vision capabilities.

## ✨ Features
- 🎙️ **Voice Mode:** Real-time, low-latency voice conversation powered by LiveKit.
- 📸 **Vision Mode:** Upload and analyze photos using local (Ollama) or cloud (Anthropic/OpenAI) models.
- 🤖 **Smart Fallback:** Automatically switches to the best available model if the chosen one fails.
- 🛠️ **Fullstack Architecture:** FastAPI backend, Next.js frontend, and a dedicated Python Voice Agent.

---

## 🚀 Quick Start (The Easiest Way)

The fastest way to get Nexa AI running is using **Docker**.

### 1. Setup Environment
Create `.env` files in the `api/` and `agent/` folders with your keys:
- `LIVEKIT_URL`, `LIVEKIT_API_KEY`, `LIVEKIT_API_SECRET`
- `ANTHROPIC_API_KEY` or `OPENAI_API_KEY`

### 2. Launch
Run the following command in the root directory:
```bash
docker compose up --build
```

### 3. Access
Open your browser to: **`http://localhost:3000`**

---

## 🛠️ Manual Installation (Without Docker)

If you prefer running the components manually:

### 1. Backend (API)
```bash
cd api
uv sync
uv run fastapi dev app/main.py
```
*Runs at `http://localhost:8000`*

### 2. Voice Agent
```bash
cd agent
uv sync
uv run python voice_agent.py start
```

### 3. Frontend (Web)
```bash
cd web
npm install
npm run dev
```
*Access at `http://localhost:3000`*

---

## 🎙️ Voice Mode Configuration
To enable the voice button, ensure your `api/.env` and `agent/.env` contain the same LiveKit credentials:
- `LIVEKIT_URL`: Your LiveKit Cloud URL (e.g., `wss://your-project.livekit.cloud`)
- `LIVEKIT_API_KEY`: Your API key from LiveKit dashboard.
- `LIVEKIT_API_SECRET`: Your API secret from LiveKit dashboard.
- `VOICE_AGENT_NAME`: `nexa-agent`

---

## 📸 Photo Capabilities
Nexa AI supports vision-capable models.
- **Local:** Run `ollama pull gemma3` or `llava`.
- **Cloud:** Use Claude 3.5 Sonnet or GPT-4o.
- **Limits:** Max 5 images per message, 10MB per image.

---

## 📐 Architecture
- **Web:** Next.js 16, React 19, Tailwind CSS, Lucide Icons.
- **API:** FastAPI, Pydantic, Uvicorn, LiveKit SDK.
- **Agent:** Python, LiveKit Agents SDK.
- **Models:** Ollama (Local), Anthropic/OpenAI (Cloud).

## 🧪 Quality Assurance
```bash
# Run API & Voice tests
cd api && uv run pytest
```
