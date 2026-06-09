# Ticket Managing System

## Project Overview
AI-powered ticket management system that automatically classifies, responds to, and routes support tickets.

## Tech Stack
- **Runtime**: Bun
- **Backend**: Express + TypeScript (`/server`)
- **Frontend**: React + TypeScript + Vite (`/client`)
- **Database**: PostgreSQL + Prisma
- **Auth**: express-session + connect-pg-simple (session-based, no JWTs)
- **AI**: Anthropic Claude API

## Monorepo Structure
```
/
├── client/        # React + Vite frontend (port 5173)
├── server/        # Express API backend (port 3001)
│   └── prisma/    # Prisma schema and migrations
└── CLAUDE.md
```

## Running the App
```bash
bun dev:server   # Express on http://localhost:3001
bun dev:client   # React on http://localhost:5173
```

## API Conventions
- All server routes are prefixed with `/api`
- Vite proxies `/api/*` → `http://localhost:3001`

## Documentation
Always use **context7** (`mcp__context7__resolve-library-id` + `mcp__context7__query-docs`) to fetch up-to-date documentation before using any library, framework, or SDK — including Express, React, Prisma, Vite, Bun, and the Anthropic SDK. Do not rely on training data for API details.
