# 🎲 D&D Voice Game Master Agent

> **Day 8 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is an immersive **Voice-Powered Dungeon Master** built using Python and the LiveKit Agents framework. It acts as a dynamic Game Master (GM) for a D&D-style adventure, narrating atmospheric stories, presenting branching choices, and responding to player decisions in real-time [web:72][attached_file:1].

The agent guides players through a mysterious coastal adventure featuring:
- **Interactive Storytelling**: Describes vivid scenes (ruined watchtowers, buried treasure boxes, hidden hatches).
- **Branching Choices**: Offers 2-3 clear options at each decision point (e.g., "Inspect box", "Approach tower", "Follow path to cottages").
- **Dynamic Narration**: Adapts the story based on player choices with immersive descriptions and consequences.
- **Game State Management**: Tracks adventure progress, prevents invalid paths, and handles restarts.
- **Atmospheric Voice**: Uses a calm, mysterious narrator voice perfect for fantasy adventures.

Built for **Murf AI Voice Agents Challenge Day 8**, this demonstrates advanced conversational state management and narrative AI [web:72].

## ✨ Key Features

- **Rich Narrative Flow**: Multi-turn adventure with meaningful choices affecting the story.
- **Voice Choice Interface**: Players say simple phrases like "Inspect box" or "Approach tower".
- **State Persistence**: Remembers player decisions across conversation turns.
- **Error Recovery**: Gracefully handles invalid inputs and offers restarts.
- **Immersive Audio**: Powered by **Murf AI Falcon Model** with a mysterious, storytelling voice.
- **Real-time Interaction**: LiveKit enables instant responses for seamless gameplay.

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
