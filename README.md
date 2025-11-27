# 💼 FAQ Sales Development Rep (SDR) & Lead Capture

> **Day 5 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is a **Voice-Activated Sales Development Representative (SDR)** built using Python and the LiveKit Agents framework. It is designed to automate the initial stages of the sales process by handling customer inquiries and capturing qualified leads in real-time.

The agent acts as a knowledgeable company representative that:
- **Answers Frequently Asked Questions (FAQs)** about products, pricing, and services.
- **Qualifies leads** by asking relevant questions to gauge customer interest.
- **Captures contact information** (Name, Email, Company) during the natural flow of conversation.
- **Logs lead data** to a structured file (simulating a CRM entry) for the sales team to follow up.

This project was built as part of the **Murf AI Voice Agents Challenge** (Day 5), demonstrating how voice AI can streamline customer engagement and lead generation [web:37][web:38].

## ✨ Key Features

- **Intelligent FAQ Handling**: Uses a predefined knowledge base (system prompt) to answer specific questions about the business accurately.
- **Natural Lead Capture**: seamlessly extracts user details (Name, Phone, Email) without breaking the conversational flow.
- **Real-time Voice Interaction**: Powered by LiveKit for low-latency, human-like conversation.
- **Data Persistence**: Automatically saves captured lead details to a `leads.csv` or `leads.txt` file.
- **Professional Persona**: Integrated with **Murf AI (Falcon Model)** to provide a polished, professional voice suitable for business contexts.

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI (Falcon Model)
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper)
- **LLM Engine**: OpenAI GPT-4o (configured with Sales & Lead Capture logic)

## 🚀 Getting Started

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

Learn more about testing voice agents in the [LiveKit testing documentation](https://docs.livekit.io/agents/build/testing/).


## License

This project is based on MIT-licensed templates from LiveKit and includes integration with Murf Falcon. See individual LICENSE files in backend and frontend directories for details.

Built for the AI Voice Agents Challenge by murf.ai
