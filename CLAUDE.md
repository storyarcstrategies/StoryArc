# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

StoryArc Strategies is a crypto/fintech content consultancy. This repo contains a local CRM MVP for tracking client prospects, outreach, and deals. The app is a **single-file HTML/CSS/JS application** — no build step, no backend, no dependencies beyond Google Fonts. Open `crm.html` directly in a browser.

## Running the app

Double-click `crm.html` or run:
```
open crm.html
```

There are no tests, no linter, no build process.

## Data layer

All data is persisted in `localStorage` under two keys:

- `storyarc_contacts` — JSON array of Contact objects
- `storyarc_touchpoints` — JSON array of Touchpoint objects

**Contact fields:** `id`, `name`, `company`, `role`, `email`, `phone`, `source` (free text), `type` (Warm | Cold | Referral), `status` (Lead | Contacted | Responded | Proposal Sent | Negotiating | Closed | Dead), `lastContactDate` (YYYY-MM-DD), `nextFollowUpDate` (YYYY-MM-DD, nullable), `notes`, `dealValue` (number, USD, nullable), `serviceInterest` (Content Function Build | Growth Content Retainer | GTM Sprint | TBD), `createdAt`, `updatedAt`.

**Touchpoint fields:** `id`, `contactId` (FK), `date` (YYYY-MM-DD), `channel` (Email | Call | LinkedIn | Meeting | Text | Other), `summary`.

## Design system

| Token | Value |
|---|---|
| Background | `#0D0D0D` |
| Surface/cards | `#161616` |
| Text primary | `#FFFFFF` |
| Text secondary | `#888888` |
| Accent | `#EF9F27` (amber — CTAs, key numbers, highlights only) |
| Border | `#2A2A2A` |
| Heading font | Syne (Google Fonts) |
| Body font | Inter (Google Fonts) |

No gradients, no shadows, no glow effects. Sharp and minimal with generous whitespace.

## Views

- **Dashboard** — open pipeline value, contacts by status, overdue follow-ups
- **All contacts** — sortable by status / last contact / next follow-up
- **Single contact** — full detail, touchpoint history, notes, edit/delete

## Seed data

On first load (empty localStorage), pre-populate two contacts:
- Pete Rizzo — `peterizzowrites@gmail.com`, Warm, Past client, Contacted, last contact 2026-05-20
- Silvia — Render Network Foundation, `silvia@renderfoundation.com`, Warm, Past client, Contacted, last contact 2026-05-20
