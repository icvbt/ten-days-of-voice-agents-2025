# 🎓 Teaching-the-Tutor: Active Recall Coach

> **Day 4 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is a **"Teach-the-Tutor" Active Recall Coach** built using Python and the LiveKit Agents framework. It flips the traditional learning model by having the user teach concepts to the AI. This method leverages the **Feynman Technique** and **Active Recall** to deepen the user's understanding of a subject.

The agent acts as a curious student who:
- **Asks the user to explain a specific topic** (e.g., Photosynthesis, Newton's Laws, Python Lists).
- **Simulates gaps in knowledge** to prompt deeper explanation from the user.
- **Asks follow-up questions** to test the user's grasp of the material.
- **Provides feedback** on how well the user explained the concept, highlighting areas that were clear or confusing.

This project was built as part of the **Murf AI Voice Agents Challenge** (Day 4), demonstrating how voice AI can be used for educational reinforcement [web:22][web:23].

## ✨ Key Features

- **Role-Reversal Learning**: The AI takes the role of a student, compelling the user to articulate their knowledge clearly.
- **Active Recall Stimulation**: By asking "Why?" and "How?" questions, the agent forces the user to retrieve information from memory.
- **Real-time Voice Interaction**: Powered by LiveKit for low-latency conversational flow.
- **Adaptive Questioning**: The agent adjusts its "confusion level" based on the clarity of the user's explanation.
- **Session Summary**: At the end of the session, the agent provides a brief review of what it "learned" from the user.

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI (Falcon Model)
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper)
- **LLM Engine**: OpenAI GPT-4o (configured with a "Curious Student" system prompt)

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
