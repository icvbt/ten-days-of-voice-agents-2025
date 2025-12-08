# 🎙️ Voice Improv Battle Host Agent

A dynamic AI voice agent that acts as the **host and referee** for interactive improv battles—where participants improvise scenes in real-time while the agent provides creative prompts, dynamic feedback, and entertaining commentary.

Built as part of **Murf AI's 10 Days of Voice Agents Challenge** (Day 10).

---

## 🎭 What is Voice Improv Battle?

Voice Improv Battle is an **entertainment-driven voice AI experience** where:

- A **host agent** introduces the battle and explains the rules
- **Participants** (voice agents or humans) receive creative scene prompts and perform improvisation
- The **host evaluates** each round with constructive feedback and energy
- **Scoring and commentary** create an engaging competitive atmosphere
- **Final verdict** announces the winner and highlights memorable moments

Example scenarios:
- "You are a customer trying to return an obviously cursed object to a very skeptical shopkeeper"
- "You are an overenthusiastic TV infomercial host selling a product that clearly does not work as advertised"
- "You are a secret agent code-named Shadow infiltrating a high-stakes pigeon poker game"

---

## ⚙️ Core Architecture

The host agent orchestrates multiple AI components working in harmony:

### 1. **Dialogue Management**
   - Dynamic conversation flow using LLM (GPT-4, Claude, etc.)
   - Real-time turn management and scene transitions
   - Context-aware response generation for engaging banter

### 2. **Voice Synthesis & Recognition**
   - **Text-to-Speech:** Murf Falcon or compatible TTS for natural narration
   - **Speech-to-Text:** Real-time transcription of participant responses
   - Low-latency audio processing (<130ms for seamless interaction)

### 3. **Orchestration Layer**
   - Manages STT → LLM → TTS pipeline
   - Handles timing, pauses, and turn-taking
   - Maintains conversation state across multiple rounds

### 4. **Evaluation Module**
   - Analyzes performance based on creativity, commitment, and humor
   - Provides real-time feedback ("Bold commitment, but try to exaggerate more!")
   - Tracks scores across rounds

---

## 🚀 Features

✨ **Dynamic Scene Generation**  
Randomly pulls creative improv prompts from a curated database to keep every battle fresh.

🎤 **Real-Time Participant Interaction**  
Listens, transcribes, and responds instantly to participant improvisation.

📊 **Intelligent Feedback System**  
Analyzes performance and delivers constructive, encouraging commentary tailored to each round.

⏱️ **Adaptive Timing Control**  
Manages round length, transition timing, and turn-taking using async event loops.

🏆 **Scorekeeping & Rankings**  
Tracks performance metrics and announces winners with memorable highlight reels.

🎬 **Entertainment-First Design**  
Host maintains energy and enthusiasm throughout, keeping the audience engaged.

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **LLM** | OpenAI GPT-4, Anthropic Claude, or custom fine-tuned model |
| **Text-to-Speech** | Murf Falcon, ElevenLabs, or PlayHT |
| **Speech-to-Text** | Google Cloud Speech-to-Text, AssemblyAI, or Deepgram |
| **Voice Framework** | RetellAI, VoiceFlow, or custom Python orchestration |
| **Backend** | Python (FastAPI/Flask) or Node.js |
| **State Management** | In-memory cache or Redis |
| **Audio Processing** | PyAudio, Pydub, or WebRTC |

---

## 📋 Getting Started

### Prerequisites
- Python 3.9+ or Node.js 16+
- API keys for:
  - OpenAI / Claude (LLM)
  - Murf Falcon or alternative TTS
  - Google Cloud / AssemblyAI (STT)
- Microphone for real-time audio input


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


Built for the AI Voice Agents Challenge by murf.ai and taksshak
