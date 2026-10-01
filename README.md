# PROJECTSYNC AI

## Intelligent Data Capture & Schedule-Linking Layer for Infrastructure Project Management

![SIH 2026](https://img.shields.io/badge/Smart%20India%20Hackathon-2026-blue)
![SIH26122](https://img.shields.io/badge/Problem%20Statement-SIH26122-orange)
![Oil India Limited](https://img.shields.io/badge/Sponsor-Oil%20India%20Limited-success)
![Status](https://img.shields.io/badge/Status-Prototype-yellow)

PROJECTSYNC AI is an AI-powered planning-to-execution intelligence platform that connects structured project schedules with real-world field execution data.

It converts DPRs, field reports, spreadsheets, and Time Agent inputs into structured **Execution Events**, matches them with **L5/L6 schedule activities**, provides confidence and explanations, and enables human verification before updating project progress.

---

## Problem

Infrastructure projects generate execution data through multiple disconnected sources such as DPRs, spreadsheets, site reports, and supervisor updates.

Common problems include:

- Fragmented field data
- Terminology mismatch
- Manual activity matching
- Delayed progress updates
- Low data quality
- Limited traceability
- Difficulty identifying downstream delays

---

## Solution

PROJECTSYNC AI creates a bridge between **Project Planning** and **Field Execution**.

```text
Project Schedule
      ↓
Field Report / DPR
      ↓
AI Extraction
      ↓
Execution Event
      ↓
L5/L6 Activity Matching
      ↓
Confidence + Explanation
      ↓
Human Verification
      ↓
Verified Progress
      ↓
Planned vs Actual
      ↓
Delay / Risk / Impact
```

---

## Core Features

### Schedule Intelligence
- L1-L6 activity hierarchy
- Schedule and activity management
- Activity dependencies
- Planned vs actual tracking

### AI Intelligence
- Field report understanding
- Information extraction
- Terminology normalization
- Execution Event generation
- Semantic activity matching
- Confidence scoring
- Explainable AI matching

### Trust & Verification
- Human-in-the-loop verification
- Exception Center
- Unmatched events
- Conflict detection
- Duplicate detection
- Stale-data detection

### Project Intelligence
- Progress tracking
- Schedule variance
- Delay detection
- Dependency impact
- Risk identification
- Evidence lineage
- Audit history

---

## L1-L6 Schedule Hierarchy

```text
L1 Project
 └── L2 Area
      └── L3 Discipline
           └── L4 Work Package
                └── L5 Activity
                     └── L6 Sub-Activity
```

---

## AI Pipeline

```text
Field Data
    ↓
Information Extraction
    ↓
Normalization
    ↓
Execution Event
    ↓
Candidate Retrieval
    ↓
Semantic Matching
    ↓
Confidence
    ↓
Explanation
    ↓
Rule Validation
    ↓
Human Review
```

AI handles interpretation and matching, while deterministic logic handles calculations, dependencies, thresholds, permissions, state changes, and audit records.

---

## Example

### Field Report

```text
Line 24 spool erection completed.
12 spools installed today.
```

### AI Extraction

```text
Discipline: Piping
Line: 24
Event: Spool Erection
Quantity: 12
```

### Match

```text
PIP-104 — Erect Line 24 Spools

Confidence: 94%

✓ Line matches
✓ Discipline matches
✓ Event type matches
✓ Location matches
```

### Result

```text
Execution Event
      ↓
Verified Activity
      ↓
Progress Update
      ↓
Schedule Impact
```

---

## Human-in-the-Loop

AI suggestions are not automatically treated as project truth.

```text
AI Suggestion
      ↓
Confidence
      ↓
Explanation
      ↓
Validation
      ↓
 ┌────┴────┐
 ↓         ↓
Verified  Review
           ↓
       Human Decision
```

This keeps critical project updates traceable and controllable.

---

## System Architecture

```text
Frontend
   ↓
API / Backend
   ↓
AI Processing + Business Logic
   ↓
PostgreSQL / Storage
   ↓
Verified Project Intelligence
```

### Technology Stack

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS
- **Backend:** Python, FastAPI
- **Database:** PostgreSQL, pgvector
- **AI:** LLM + Embeddings
- **Processing:** PyMuPDF, pandas, openpyxl
- **Infrastructure:** Docker / Supabase

---

## Project Structure

```text
PROJECTSYNC-AI/
├── frontend/
├── backend/
├── data/
├── tests/
├── docs/
├── .env.example
├── docker-compose.yml
└── README.md
```

---

## Setup

### Clone

```bash
git clone <REPOSITORY_URL>
cd <REPOSITORY_NAME>
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

### Backend

```bash
cd backend
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run:

```bash
uvicorn main:app --reload
```

---

## Environment Variables

Create `.env` from `.env.example`.

```env
DATABASE_URL=
AI_API_KEY=
SUPABASE_URL=
SUPABASE_ANON_KEY=
JWT_SECRET=
```

Never commit real API keys or credentials.

---

## Project Vision

```text
PLAN
 ↓
FIELD
 ↓
UNDERSTAND
 ↓
MATCH
 ↓
VERIFY
 ↓
UPDATE
 ↓
IMPACT
 ↓
ACT
```

### PROJECTSYNC AI

**From fragmented field execution to trusted, schedule-linked project intelligence.**

---

## Team

**Team-VernoNix**

**Smart India Hackathon 2026**  
**Problem ID: SIH26122**  
**Organization: Oil India Limited**
