# 🧠 Day 8 – LLM Query Voice Agent

> Voice agent that routes natural language questions to an LLM “query endpoint” and returns concise, helpful answers in real time.

## 📖 Overview

This project implements a **Day 8 Voice Agent** for the Murf AI “Ten Days of Voice Agents 2025” challenge. The agent acts like a conversational front-end for an LLM query endpoint: the user speaks a question, the agent sends a structured query to an LLM, then returns a clear, spoken answer with optional follow-up suggestions [web:1][web:33].

The agent is designed to:
- Accept open-ended user questions via voice (e.g., “Explain JWT in simple terms” or “Summarize the pros and cons of microservices”).
- Turn those questions into a well-formed LLM request with instructions on answer style.
- Read back concise, structured answers using Murf Falcon TTS.
- Maintain lightweight context so follow-up questions like “Explain that part again in one line” still make sense.

It showcases how to build a reusable “LLM query layer” on top of your existing Day 1–7 agents so they can answer deeper knowledge questions on demand [web:33].

## ✨ Key Features

- Natural language Q&A over voice, backed by an LLM query endpoint.
- System prompts to keep answers:
  - Concise and structured.
  - Free of sensitive or disallowed content.
  - Easy to understand for non-experts.
- Lightweight conversation memory for short follow-up questions.
- Real-time streaming audio with low latency.
- Simple abstraction so other agents (barista, wellness, SDR, etc.) can call this skill.
- 
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
