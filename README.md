# deterministic-parametric-kernel
Deterministic, compiler-style parametric geometry architecture (documentation &amp; proofs


# CADai — Reality→Digital Intelligence (MVP)

This repository contains a minimal production-quality MVP for CADai: a Reality-to-Digital intelligence demo where users can select objects from a camera feed and persist selections to the backend for history and visualization.

## Project layout

- backend/ — Node + TypeScript + Express API
  - src/ — TypeScript source
  - data/ — persisted history (JSON)
- frontend/ — static web UI (HTML/CSS/JS)

## Features

- Camera access (browser) with selection rectangle overlay
- Send selections (`/objects`) to backend
- Persisted history at `data/history.json`
- Health check: `GET /health`
- History endpoints: `GET /history`, `DELETE /history`

## Run backend (development)

From `backend/`:

```bash
npm install
npm run dev
```

The server listens on port `4000` by default (use `PORT` env to override).

## Run frontend

Open `frontend/index.html` in your browser (Chrome/Edge/Firefox). For camera access use a secure context (https or localhost). The frontend expects the backend at `http://localhost:4000`.

## API (summary)

- GET /health — status
- POST /objects — record selection { id, label, bbox: {x,y,w,h}, meta }
- GET /objects — list selections
- GET /history — same as /objects
- DELETE /history — clear history

## Design notes

- Backend uses lightweight JSON file persistence for the MVP (`fs-extra`) to keep demo simple.
- Routes/controllers/services are separated for clarity and future scaling.
- Minimal error handling and logging (morgan) are included.

If you'd like, I can:
- Add tests
- Replace file storage with a small DB (SQLite)
- Add CI config and linting

*** End of README ***
