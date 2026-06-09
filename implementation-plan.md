# Implementation Plan

## Phase 1 — Project Setup

- [x] Initialise monorepo structure (`/client`, `/server`)
- [x] Set up Express server with TypeScript (Bun runtime)
- [x] Set up React app with TypeScript (Vite)
- [x] Set up PostgreSQL database (Prisma schema initialised)

---

## Phase 2 — Authentication

### Backend

- [ ] `User` schema: id, email, password_hash, role (admin | agent), created_at
- [ ] Seed admin account on first run
- [ ] Set up `express-session` + `connect-pg-simple`
- [ ] `POST /auth/login` — validate credentials, create session
- [ ] `POST /auth/logout` — destroy session
- [ ] `GET /auth/me` — return current session user
- [ ] `requireAuth` middleware
- [ ] `requireAdmin` middleware

### Frontend

- [ ] Login page
- [ ] Session-aware routing (redirect unauthenticated users)
- [ ] Logout button

---

## Phase 3 — User Management (Admin)

### Backend

- [ ] `GET /users` — list all agents (admin only)
- [ ] `POST /users` — create agent account (admin only)
- [ ] `DELETE /users/:id` — remove agent (admin only)

### Frontend

- [ ] Agents list page (admin)
- [ ] Create agent form
- [ ] Delete agent action

---

## Phase 4 — Tickets (Core)

### Backend

- [ ] `Ticket` schema: id, subject, body, status (open | resolved), category, student_email, assigned_to (agent id), created_at, updated_at
- [ ] `POST /tickets` — create ticket
- [ ] `GET /tickets` — list tickets (admin: all; agent: assigned only)
- [ ] `GET /tickets/:id` — ticket detail
- [ ] `PATCH /tickets/:id` — update status / respond

### Frontend

- [ ] Student-facing ticket submission form
- [ ] Ticket list page (role-aware)
- [ ] Ticket detail page
- [ ] Reply / close ticket actions

---

## Phase 5 — Admin: Ticket Assignment

### Backend

- [ ] `PATCH /tickets/:id/assign` — assign ticket to an agent (admin only)

### Frontend

- [ ] Assign ticket dropdown on ticket detail (admin)
- [ ] Unassigned tickets view (admin dashboard)

---

## Phase 6 — AI Features

### Backend

- [ ] Integrate Anthropic Claude API
- [ ] On ticket create: classify ticket into category using AI
- [ ] On ticket create: generate a response using knowledge base
- [ ] If AI is confident → send response automatically + mark resolved
- [ ] If AI is not confident → hold ticket as open, flag for agent
- [ ] `GET /tickets/:id/summary` — AI-generated ticket summary

### Frontend

- [ ] Display AI-generated category on ticket detail
- [ ] Display AI summary on ticket detail
- [ ] Show "AI responded" vs "Awaiting agent" indicator

---

## Phase 7 — Email Ingestion

- [ ] Choose inbound email provider (SendGrid / Mailgun)
- [ ] Set up inbound email webhook endpoint
- [ ] Parse inbound email into a ticket (subject → title, body → description, from → student_email)
- [ ] Send AI response back via email

---

## Phase 8 — Polish & Dashboard

### Backend

- [ ] Ticket filtering by status and category
- [ ] Ticket sorting (newest, oldest)
- [ ] `GET /dashboard/stats` — counts by status (admin)

### Frontend

- [ ] Filter and sort controls on ticket list
- [ ] Admin dashboard with ticket stats (open, resolved, unassigned)
- [ ] Loading and error states throughout
