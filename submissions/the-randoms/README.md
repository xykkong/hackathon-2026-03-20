# LexiCoach

LexiCoach is a real-time vocabulary practice AI coach built for the Preply hackathon on top of Agora Conversational AI. Learners practice target words in natural spoken conversation with a video avatar.

## What It Does

- Personalizes practice by learner level, theme, and known words
- Runs a live spoken session with an AI tutor avatar
- Focuses each session on target vocabulary usage
- Gives corrective feedback and asks for natural retries

## Repository Layout

```text
submissions/the-randoms/
├── README.md
├── HOW_WE_BUILT.md
├── demo.txt
├── assets/                  # Screenshots and brand assets
├── docs/                    # Project documentation
├── design/                  # Design notes and references
└── src/
    ├── react-video-client-avatar/  # Frontend (Next.js)
    ├── simple-backend/             # Python backend used in demo
    └── server-custom-llm/          # Custom LLM backend samples
```

## Quickstart

### Prerequisites

- Node.js 20+
- Python 3.10+
- Agora App ID + App Certificate
- LLM key (OpenAI-compatible)
- TTS/avatar provider credentials

### 1) Configure backend env

```bash
cd submissions/the-randoms/src/simple-backend
cp .env.example .env
```

Edit `.env` and set required `VIDEO_*` values.

### 2) Run backend

```bash
cd submissions/the-randoms/src/simple-backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements-local.txt
python3 -u local_server.py
```

Backend: `http://localhost:8082`

### 3) Run frontend

```bash
cd submissions/the-randoms/src/react-video-client-avatar
npm install --legacy-peer-deps
npm run dev
```

Frontend: `http://localhost:8084`

### 4) Try the app

- Open `http://localhost:8084`
- Click **Start Call**
- Talk with the avatar coach
- Restart call after any prompt or env change

## Tech Stack

- Frontend: Next.js 16, React, TypeScript, Tailwind CSS
- Realtime transport: Agora RTC
- Realtime signaling/events: Agora RTM
- Agent orchestration: Agora AI Agent API (Agora Conversational AI)
- Backend: Python + Flask (`src/simple-backend`)
- LLM: OpenAI `gpt-4o-mini`
- Text-to-speech: ElevenLabs TTS
- Avatar provider: Anam avatar
- Optional biomarker integration: THYMIA (disabled for demo due to Cloudflare `429` errors)

## Demo

See `demo.txt` in this folder for the demo video link.

## Pre-Submit Checklist

- [x] Team folder exists under `submissions/the-randoms`
- [x] `README.md` includes setup and run instructions
- [x] `HOW_WE_BUILT.md` documents AI process, prompts, model choices, and iteration
- [x] Source code is organized under `src/`
- [x] `demo.txt` includes the demo video link

## Judge Notes

- Main runnable path: `submissions/the-randoms/src/`
- Primary demo stack: `src/simple-backend` + `src/react-video-client-avatar`
- Additional advanced reference implementation: `src/server-custom-llm`
- Authoritative docs for setup/submission: `README.md`, `HOW_WE_BUILT.md`, `docs/CODE_ORGANIZATION.md`, `docs/SUBMISSION_CHECKLIST.md`
- `design/` contains research/reference notes and may include upstream example paths
