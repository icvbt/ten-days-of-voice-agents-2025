# 🌿 Health & Wellness Voice Companion

> **Day 3 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is a **Daily Health & Wellness Voice Companion** built using Python and the LiveKit Agents framework [web:13]. It serves as an empathetic AI wellness coach that engages users in supportive conversations about their mental and physical health.

The agent is designed to:
- **Check in on daily wellness** by asking about energy levels, mood, and overall well-being.
- **Set achievable goals** based on the user's current state and capacity.
- **Provide personalized support** with empathetic responses tailored to the user's emotional state.
- **Track wellness progress** by logging daily check-ins, goals, and user interactions.
- **Offer gentle guidance** for stress management, productivity, and self-care activities.

This project was built as part of the **Murf AI Voice Agents Challenge**, demonstrating compassionate AI design with real-time voice interaction capabilities [web:15].

## ✨ Key Features

- **Empathetic Conversations**: Recognizes low energy states and adjusts goal-setting accordingly.
- **Real-time Voice Interaction**: Uses LiveKit for seamless audio streaming and natural dialogue flow.
- **Context-Aware Responses**: Remembers conversation context to provide relevant support throughout the session.
- **Wellness Logging**: Automatically saves daily check-ins, mood assessments, and goals to a `wellness_log.txt` file [web:13].
- **Human-like TTS**: Integrated with **Murf AI (Falcon Model)** for warm, supportive voice responses.
- **Mental Health Support**: Provides guided suggestions, breathing exercises, and achievable micro-tasks [web:17].

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI (Falcon Model)
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper)
- **LLM Engine**: OpenAI GPT-4o (for conversational intelligence and empathy)

## Repository Structure

This is a **monorepo** that contains both the backend and frontend for building voice agent applications. It's designed to be your starting point for each day's challenge task.

```
falcon-tdova-nov25-livekit/
├── backend/          # LiveKit Agents backend with Murf Falcon TTS
├── frontend/         # React/Next.js frontend for voice interaction
├── start_app.sh      # Convenience script to start all services
└── README.md         # This file
```

### Backend

The backend is based on [LiveKit's agent-starter-python](https://github.com/livekit-examples/agent-starter-python) with modifications to integrate **Murf Falcon TTS** for ultra-fast, high-quality voice synthesis.

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

Learn more about testing voice agents in the [LiveKit testing documentation](https://docs.livekit.io/agents/build/testing/).

## 📊 Wellness Log Output

The agent automatically saves conversation summaries to `wellness_log.txt`, including:
- Current mood and energy levels
- Goals set during the session
- Recommended actionable steps
- Recap of the day's wellness focus [web:13][web:18]

## 🎯 Use Cases

- **Mental Health Support**: Daily check-ins for individuals managing stress or low motivation [web:17].
- **Productivity Coaching**: Setting micro-goals based on current capacity.
- **Wellness Tracking**: Maintaining a conversational log of daily emotional and physical states.
- **Telemedicine Integration**: Complementing healthcare services with voice-based wellness monitoring [web:17].

## 🤝 Acknowledgments

- **Murf AI**: For organizing the "Ten Days of Voice Agents" challenge and providing the Falcon TTS model.
- **LiveKit**: For the robust real-time audio infrastructure.
- **Community**: Thanks to fellow developers participating in the challenge for shared learning and inspiration.

---

*Developed with care for Day 3 of the Murf AI Voice Agents Challenge - 2025* 🌱- ##taksshak 2025


## Contributing & Community

This is a challenge repository, but we encourage collaboration and knowledge sharing!

- Share your solutions and learnings on GitHub
- Post about your progress on LinkedIn
- Join the [LiveKit Community Slack](https://livekit.io/join-slack)
- Connect with other challenge participants

## License

This project is based on MIT-licensed templates from LiveKit and includes integration with Murf Falcon. See individual LICENSE files in backend and frontend directories for details.

## Have Fun!

Remember, the goal is to learn, experiment, and build amazing voice AI agents. Don't hesitate to be creative and push the boundaries of what's possible with Murf Falcon and LiveKit!

Good luck with the challenge!

---

Built for the AI Voice Agents Challenge by murf.ai
