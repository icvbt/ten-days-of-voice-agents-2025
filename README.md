# 🛒 Day 9 – E‑commerce Voice Agent (Agentic Commerce Inspired)

> Voice-driven shopping assistant that understands what you want to buy, browses a catalog, and places real orders via voice.

## 📖 Project Overview

This project implements an **E‑commerce Voice Agent** inspired by the Agentic Commerce Protocol (ACP), built using Python, LiveKit Agents, and Murf Falcon TTS. [web:83][web:89]  
The agent acts as a voice-first shopping assistant that can search products, filter options, manage a cart, and place orders end-to-end using natural conversation. [web:83][web:86]

The agent can:
- Understand intents like “show me mugs under ₹500” or “I want a black hoodie in size L”. [web:86]
- Browse a structured product catalog (ID, name, price, category, tags). [web:83]
- Create and update cart/order objects with product IDs, quantities, prices, and timestamps. [web:86]
- Confirm orders and return an order ID plus final amount. [web:83]
- Answer questions like “What did I just buy?” or “What’s in my cart?”. [web:86]

Built as the **Day 9 submission** for the Murf AI Voice Agents Challenge – turning voice directly into commerce. [web:83][web:88]

## ✨ Key Features

- Natural-language product discovery (categories, colors, sizes, budgets). [web:86]
- Voice-only cart management: add, update, remove, and review items. [web:83]
- Lightweight “merchant layer” / ACP-style backend for catalog + orders. [web:86][web:89]
- Orders persisted in JSON so each purchase is stored and queryable. [web:86]
- Fast, human-like narration using **Murf Falcon** real-time TTS. [web:12][web:87]
- Real-time, low-latency interaction powered by **LiveKit Agents**. [web:77][web:87]

## 🛠️ Tech Stack

- Language: Python 3.9+  
- Realtime framework: LiveKit Agents [web:77]  
- TTS: Murf AI Falcon (Realtime API) [web:12][web:87]  
- STT: Deepgram / Whisper (configurable) [web:83]  
- LLM: OpenAI GPT‑4o for intent + slot extraction [web:83]  
- Storage: Local JSON files for products and orders [web:86]
 
### Prerequisites

Make sure you have the following installed:

- Python 3.9+ with [uv](https://docs.astral.sh/uv/) package manager
- Node.js 18+ with pnpm
- [LiveKit CLI](https://docs.livekit.io/home/cli/cli-setup) (optional but recommended)
- [LiveKit Server](https://docs.livekit.io/home/self-hosting/local/) for local development

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd falcon-tdova-nov25-livekit
```

### 2. Backend Setup

```bash
cd backend

# Install dependencies
uv sync

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with your credentials:
# - LIVEKIT_URL
# - LIVEKIT_API_KEY
# - LIVEKIT_API_SECRET
# - MURF_API_KEY (for Falcon TTS)
# - GOOGLE_API_KEY (for Gemini LLM)
# - DEEPGRAM_API_KEY (for Deepgram STT)

# Download required models
uv run python src/agent.py download-files
```

For LiveKit Cloud users, you can automatically populate credentials:

```bash
lk cloud auth
lk app env -w -d .env.local
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
pnpm install

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with the same LiveKit credentials
```

### 4. Run the Application

#### Install livekit server

```bash
brew install livekit
```

You have two options:

#### Option A: Use the convenience script (runs everything)

```bash
# From the root directory
chmod +x start_app.sh
./start_app.sh
```

This will start:

- LiveKit Server (in dev mode)
- Backend agent (listening for connections)
- Frontend app (at http://localhost:3000)

#### Option B: Run services individually

```bash
# Terminal 1 - LiveKit Server
livekit-server --dev

# Terminal 2 - Backend Agent
cd backend
uv run python src/agent.py dev

# Terminal 3 - Frontend
cd frontend
pnpm dev
```

Then open http://localhost:3000 in your browser!


## Documentation & Resources

- [Murf Falcon TTS Documentation](https://murf.ai/api/docs/text-to-speech/streaming)
- [LiveKit Agents Documentation](https://docs.livekit.io/agents)
- [Original Backend Template](https://github.com/livekit-examples/agent-starter-python)
- [Original Frontend Template](https://github.com/livekit-examples/agent-starter-react)

## Testing

The backend includes a comprehensive test suite:

```bash
cd backend
uv run pytest
```

## License

This project is based on MIT-licensed templates from LiveKit and includes integration with Murf Falcon. See individual LICENSE files in backend and frontend directories for details.

Built for the AI Voice Agents Challenege by taksshak
