# 🛒 Food & Grocery Ordering Voice Agent with Cart Management

> **Day 7 Submission for the "Ten Days of Voice Agents 2025" Challenge**

## 📖 Project Overview

This project is an intelligent **Food & Grocery Voice Assistant** built using Python and the LiveKit Agents framework. It acts as a virtual shop assistant capable of managing a shopping cart in real-time, handling complex orders, and simulating a checkout process for a grocery store or restaurant [web:58][web:68].

The agent is designed to:
- **Search & Recommend Items**: Browse a simulated inventory (e.g., "Dr. Abhishek's Indian Grocery Store") to find specific products.
- **Manage a Shopping Cart**: Add, update, or remove items from a persistent cart using natural voice commands (e.g., "Add 5 packets of Maggie").
- **Calculate Real-time Totals**: Instantly update the cart total as items are modified.
- **Handle "Out of Stock" Scenarios**: gracefully inform users when an item is unavailable.
- **Process Checkout**: Collect user details (Name, Address) and confirm the order, generating a unique order ID.
- **Track Order Status**: Check the status of past orders (e.g., "Shipped", "Out for Delivery") using an order ID.

This project was built as part of the **Murf AI Voice Agents Challenge** (Day 7), demonstrating advanced state management and transactional voice AI capabilities [web:58].

## ✨ Key Features

- **Dynamic Cart Management**: Supports multi-turn conversations to build a complete shopping list.
- **Inventory Awareness**: Checks product availability before adding to the cart.
- **Contextual Updates**: Understands requests like "Change that to 10 packets" based on the previous turn.
- **Real-time Voice Interaction**: Powered by LiveKit for low-latency, human-like conversation.
- **Data Persistence**: Saves orders to a local JSON/Text file database for retrieval and status tracking.
- **Realistic TTS**: Integrated with **Murf AI (Falcon Model)** for a professional and friendly shop assistant voice.

## 🛠️ Tech Stack

- **Programming Language**: Python
- **Voice Framework**: [LiveKit Agents](https://docs.livekit.io/agents/)
- **Text-to-Speech (TTS)**: Murf AI (Falcon Model)
- **Speech-to-Text (STT)**: Deepgram (or OpenAI Whisper)
- **LLM Engine**: OpenAI GPT-4o (with Function Calling for cart operations)

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

---

Built for the AI Voice Agents Challenge by takshak
