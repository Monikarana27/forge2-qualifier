# Architecture

## Agent Workflow

```
Human → #agent-control (Slack)
           ↓
        Hermes (planner)
           ↓ delegates via Slack
        OpenClaw (coder)
           ↓ writes files, runs commands
        kanban-api / kanban-ui
```

## Slack Channels

| Channel | Purpose |
|---------|---------|
| #agent-control | Main human ↔ agent communication |

## Agents

### Hermes
- Planning & task breakdown
- Delegates coding tasks to OpenClaw
- Runs in: WSL Ubuntu (`hermes gateway run`)
- Model: Ollama qwen2.5:1.5b via `http://192.168.240.1:11434/v1`

### OpenClaw
- Executes code, runs shell commands
- Reports progress back to Slack
- Runs in: Windows (`openclaw gateway start`)
- Model: Ollama qwen2.5:1.5b via `http://localhost:11434`

## Model Routing

```
Hermes    → Ollama qwen2.5:1.5b (local, free)
OpenClaw  → Ollama qwen2.5:1.5b (local, free)
```

## Stack

```
Frontend  →  React + Vite  →  Vercel
Backend   →  Laravel + SQLite  →  Render
LLM       →  Ollama (local)
Agents    →  Hermes + OpenClaw
Comms     →  Slack Socket Mode
```
