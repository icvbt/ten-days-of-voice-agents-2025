On Day 2 
We turn the starter agent into a coffee shop barista that can take voice orders and show a neat text summary.
> **Day 2 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is a **Voice-Activated Coffee Shop Barista** built using Python and the LiveKit Agents framework. It serves as an intelligent conversational interface that mimics a real-world barista interaction.

The agent is designed to:
- **Greet customers** warmly and ask for their order.
- **Process voice commands** to identify coffee preferences (e.g., Latte, Cappuccino) and customizations (e.g., skim milk, extra sugar).
- **Capture user details**, specifically asking for the customer's name to personalize the experience.
- **Log orders** persistently (simulated database entry) for backend processing.

This project was built as part of the **Murf AI Voice Agents Challenge**, demonstrating the integration of low-latency Text-to-Speech (TTS) with real-time conversational logic.

## ✨ Key Features

- **Real-time Voice Interaction**: Uses LiveKit for low-latency audio streaming.
- **Human-like TTS**: Integrated with **Murf AI (Falcon Model)** for natural-sounding voice responses.
- **Order Management Logic**: Capable of handling multi-turn conversations to construct a complete order.
- **Data Persistence**: Saves completed orders to a local text log/database file.

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper, depending on configuration)
- **LLM Engine**: OpenAI GPT-4o (for conversational logic)

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:
- Python 3.9 or higher
- A LiveKit Cloud project (or local instance)
- API Keys for:
  - LiveKit
  - OpenAI
  - Murf AI

Once running, you can connect to the agent using the LiveKit Playground or your custom frontend to place your coffee order!

# AI Voice Agents Challenge

Welcome to the **AI Voice Agents Challenge** by [murf.ai](https://murf.ai)!

**Features:**

- Complete voice AI agent framework using LiveKit Agents
- Murf Falcon TTS integration for fastest text-to-speech
- LiveKit Turn Detector for contextually-aware speaker detection
- Background voice cancellation
- Integrated metrics and logging
- Complete test suite with evaluation framework
- Production-ready Dockerfile

[→ Backend Documentation](./backend/README.md)

### Frontend

The frontend is based on [LiveKit's agent-starter-react](https://github.com/livekit-examples/agent-starter-react), providing a modern, beautiful UI for interacting with your voice agents.

**Features:**

- Real-time voice interaction with LiveKit Agents
- Camera video streaming support
- Screen sharing capabilities
- Audio visualization and level monitoring
- Light/dark theme switching
- Highly customizable branding and UI

[→ Frontend Documentation](./frontend/README.md)

## Quick Start

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

## Daily Challenge Tasks

Each day, you'll receive a new task that builds upon your voice agent. The tasks will help you:

- Implement different personas and conversation styles
- Add custom tools and capabilities
- Integrate with external APIs
- Build domain-specific agents (customer service, tutoring, etc.)
- Optimize performance and user experience

**Stay tuned for daily task announcements!**

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

## 🤝 Acknowledgments

- **Murf AI**: For organizing the "Ten Days of Voice Agents" challenge and providing the Falcon TTS model.
- **LiveKit**: For the robust real-time audio infrastructure.
- **Community**: Thanks to fellow developers participating in the challenge for the shared learning experience.

***

*Developed by taksshak - 2025*

Learn more about testing voice agents in the [LiveKit testing documentation](https://docs.livekit.io/agents/build/testing/).

## Contributing & Community

This is a challenge repository, but we encourage collaboration and knowledge sharing!

- Share your solutions and learnings on GitHub
- Post about your progress on LinkedIn
- Join the [LiveKit Community Slack](https://livekit.io/join-slack)
- Connect with other challenge participants

## License

This project is based on MIT-licensed templates from LiveKit and includes integration with Murf Falcon. See individual LICENSE files in backend and frontend directories for details.

Built for the AI Voice Agents Challenge by murf.ai
