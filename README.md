# Linux Server Monitoring & Alerting System — Frontend

React dashboard for the Linux Server Monitoring & Alerting System. Displays live server status, real-time CPU/RAM/disk metrics, historical charts, and active alerts.

**Backend repo (full project details, architecture, API docs):** [monitoring-backend](https://github.com/naren-wwcd/monitoring-backend)

## Features

- **Live dashboard** — auto-refreshing (10s) overview of all monitored servers with Up/Down counts
- **Per-server cards** — color-coded CPU/RAM/disk usage with a live sparkline chart
- **Server detail view** — full historical charts (24h / 7d / 30d) for CPU, RAM, disk, and network, plus uptime and process count
- **Active alerts panel** — real-time display of ongoing threshold breaches and server-down alerts, sourced from the backend's alerting engine
- **Dockerized** — multi-stage build serving a production bundle via nginx

## Tech Stack

- React (Vite)
- react-router-dom
- recharts (charts and sparklines)
- Plain CSS with custom properties (theming)

## Running the Project

### Option 1 — Docker Compose (from the backend repo, recommended)

The frontend is one service in the full stack's `docker-compose.yml` (see the backend repo). Running:
```bash
docker compose up --build
```
serves this frontend at `http://localhost:8082`, fully wired to the backend API.

### Option 2 — Local development

```bash
npm install
npm run dev
```

Runs on `http://localhost:5173` by default. Requires the backend API running and reachable at `http://localhost:8080` (see backend repo for setup).

### Option 3 — Standalone Docker build

```bash
docker build -t monitoring-frontend .
docker run -p 8082:80 monitoring-frontend
```

## Project Structure

src/
App.jsx # Routing setup
Dashboard.jsx # Main dashboard view
ServerCard.jsx # Per-server summary card
ServerDetail.jsx # Detailed server view with historical charts
colors.js # Shared color-threshold logic


## Project Status

This is an actively developed portfolio project. See the [backend repo](https://github.com/naren-wwcd/monitoring-backend) for full architecture details, API documentation, and setup instructions.
