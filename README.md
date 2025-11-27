# 🚨 Fraud Alert Voice Agent

> **Day 6 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is an intelligent **Fraud Detection & Prevention Voice Agent** built using Python and the LiveKit Agents framework. It acts as an automated bank security representative, capable of calling customers in real-time to verify suspicious transactions and take immediate action to secure their accounts [web:53][web:55].

The agent is designed to:
- **Trigger Outbound Calls**: Automatically initiates a call when a high-risk transaction flag is raised.
- **Verify Identity**: Authenticates the user via security questions or PIN verification before discussing sensitive details.
- **Confirm Activity**: Reads out transaction details (amount, merchant, location) and asks the user to authorize or deny the charge.
- **Execute Security Protocols**: If fraud is confirmed, the agent can immediately block the card and log the incident for the fraud department.
- **Provide Reassurance**: Uses a calm, professional, and trustworthy voice to guide users through stressful security alerts.

This project was built as part of the **Murf AI Voice Agents Challenge** (Day 6), demonstrating how AI can enhance financial security and customer trust [web:53][web:56].

## ✨ Key Features

- **Proactive Security**: Reduces fraud response time from hours to seconds by automating the verification process.
- **Context-Aware Dialogue**: Powered by LLMs to handle anxious or confused customer responses naturally.
- **Real-time Action**: Integrates with backend systems to "block" cards instantly during the call.
- **Secure Data Handling**: Designed to mask sensitive information during the conversation.
- **Human-like Latency**: Powered by LiveKit for near-instantaneous voice responses.
- **Realistic Voice Persona**: Uses **Murf AI (Falcon Model)** to ensure the agent sounds authoritative yet empathetic.

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI (Falcon Model)
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper)
- **LLM Engine**: OpenAI GPT-4o (with strict system prompts for security compliance)


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
