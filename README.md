# Forge 2 Qualifier — Kanban Board

A Trello-style Kanban board built by two AI agents collaborating over Slack.

## What the App Does

Full-featured Kanban board with:
- Boards → Lists → Cards hierarchy
- Drag-and-drop cards between lists
- Edit card title & description
- Tags/labels
- Assign members
- Due dates with overdue highlight

## Models Used

| Agent | Model |
|-------|-------|
| Hermes (planner) | Ollama qwen2.5:1.5b (local) |
| OpenClaw (coder) | Ollama qwen2.5:1.5b (local) |

## Why These Models

- **Free**: Ollama runs locally, zero API cost
- **Fast enough**: qwen2.5:1.5b fits in CPU RAM and responds within Slack's timeout window
- **No external dependency**: Works offline, no rate limits, no quota issues

## Tech Stack

- **Backend**: Laravel (PHP) + SQLite
- **Frontend**: React + Vite
- **Agent Communication**: Slack (#agent-control)
- **Agents**: Hermes (WSL Ubuntu) + OpenClaw (Windows)
- **LLM**: Ollama qwen2.5:1.5b

## How to Run Locally

### Backend
```bash
cd backend
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

### Frontend
```bash
cd frontend
npm install
npm run dev
```

## Live URL

https://kanban-ui.vercel.app (frontend)

## GitHub Repo

https://github.com/Monikarana27/forge2-qualifier
