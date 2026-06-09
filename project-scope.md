# AI-Powered Ticket Management System

## Problem

We receive hundreds of support emails daily. Our agents manually read, classify, and respond to each ticket - which is slow and leads to impersonal, canned responses.

## Solution

Build a ticket management system that uses AI to automatically classify, respond to, and route support tickets - delivering faster, more personalized responses to students while freeing up agents for complex issues.

## Ticket Statuses

- **Open** — ticket has been received and is awaiting action
- **Resolved** — an answer has been sent (by AI or agent); can be marked by the AI
- **Closed** — TBD (distinction from Resolved not yet defined)

## Ticket Categories

- General Question
- Technical Question
- Refund Request

## Ticket Creation

Tickets can be created two ways:
- A student submits via a form in the app
- An inbound support email is automatically ingested

## AI Behaviour

- The AI auto-classifies each ticket into a category
- The AI generates and **sends a response automatically** to the student using a knowledge base
- If the AI cannot find a confident answer, the ticket is **held and assigned to an agent** for manual handling
- The AI can mark a ticket as Resolved after sending a response

> **TBD:** Knowledge base — structure, format, and who maintains it

## Routing & Assignment

- Tickets are **manually assigned** by an admin to a specific agent
- All routing decisions are made by the admin, not the AI

## Roles

| Role  | Capabilities |
|-------|-------------|
| Admin | Deployed with the system; create and manage agents; assign tickets; manage all tickets |
| Agent | Created by admin; view and manage tickets |

- The system is bootstrapped with a single admin account
- Admins can create additional agent accounts

## Features

- Receive support emails and create tickets
- Student-facing submission form
- Auto-generate and send responses using a knowledge base
- AI fallback: hold ticket and assign to agent when AI confidence is low
- Ticket list with filtering and sorting
- Ticket detail view
- AI-powered ticket classification
- AI summaries
- AI-suggested replies
- Admin: manual ticket assignment to agents
- User management (admin only)
- Dashboard to view and manage all tickets
