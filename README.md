# PROJECTSYNC AI

### Intelligent Data Capture & Schedule-Linking Layer for Infrastructure Project Management

> **Smart India Hackathon 2026 — Problem ID: SIH26122**  
> **Organization: Oil India Limited**  
> **Domain: Smart Automation**

PROJECTSYNC AI is an AI-powered planning-to-execution intelligence platform designed to convert fragmented field execution information into trusted, schedule-linked project progress.

The system acts as an intelligent execution-data layer between structured project schedules and real-world field execution. It interprets DPRs, field reports, spreadsheets, and Time Agent inputs, converts them into structured **Execution Events**, identifies the most relevant **L5/L6 schedule activities**, assigns confidence and explainable reasons, routes uncertain cases to human reviewers, and connects verified execution data to progress, variance, dependencies, risks, evidence, and audit history.

---

## Table of Contents

- [Project Overview](#1-project-overview)
- [Problem Statement](#2-problem-statement)
- [Proposed Solution](#3-proposed-solution)
- [Core Intelligence](#4-core-intelligence)
- [End-to-End Workflow](#5-end-to-end-workflow)
- [Key Features](#6-key-features)
- [Schedule Hierarchy](#7-schedule-hierarchy)
- [Execution Event Model](#8-execution-event-model)
- [AI Processing Architecture](#9-ai-processing-architecture)
- [AI vs Deterministic Logic](#10-ai-vs-deterministic-logic)
- [Confidence & Explainability](#11-confidence--explainability)
- [Human-in-the-Loop Verification](#12-human-in-the-loop-verification)
- [Exception Center](#13-exception-center)
- [Progress & Schedule Intelligence](#14-progress--schedule-intelligence)
- [Dependency & Risk Intelligence](#15-dependency--risk-intelligence)
- [Evidence & Auditability](#16-evidence--auditability)
- [Time Agent](#17-time-agent)
- [User Roles](#18-user-roles)
- [System Architecture](#19-system-architecture)
- [Technology Stack](#20-technology-stack)
- [Database Model](#21-database-model)
- [API Architecture](#22-api-architecture)
- [Project Structure](#23-project-structure)
- [Installation & Setup](#24-installation--setup)
- [Environment Variables](#25-environment-variables)
- [Running the Application](#26-running-the-application)
- [Demo Workflow](#27-demo-workflow)
- [Example Input & Output](#28-example-input--output)
- [AI Safety Principles](#29-ai-safety-principles)
- [Testing](#30-testing)
- [Dataset & Demonstration Data](#31-dataset--demonstration-data)
- [MVP Scope](#32-mvp-scope)
- [Future Scope](#33-future-scope)
- [Screens & Product Experience](#34-screens--product-experience)
- [Project Differentiation](#35-project-differentiation)
- [Limitations](#36-limitations)
- [Team](#37-team)
- [License](#38-license)

---

# 1. Project Overview

Infrastructure projects generate large amounts of structured planning information and unstructured execution information.

The baseline schedule may contain thousands of L5/L6 activities, while actual site progress may be reported through:

- Daily Progress Reports (DPRs)
- Site diaries
- Spreadsheets
- Supervisor updates
- Field text
- Time-based updates
- Evidence attachments

These sources often use different terminology, different levels of detail, and different reporting cadences.

PROJECTSYNC AI provides the bridge between these two worlds.

```text
STRUCTURED PLAN
       |
       v
L1-L6 PROJECT SCHEDULE
       |
       |          FIELD REALITY
       |               |
       |               v
       |        DPR / REPORT / TIME AGENT
       |               |
       +-------+-------+
               |
               v
       AI INFORMATION EXTRACTION
               |
               v
        EXECUTION EVENT
               |
               v
       ACTIVITY MATCHING
               |
               v
     CONFIDENCE + EXPLANATION
               |
               v
        RULE VALIDATION
               |
          +----+----+
          |         |
       High       Uncertain
          |         |
          v         v
       Verify    Human Review
          |         |
          +----+----+
               |
               v
       VERIFIED PROGRESS
               |
               v
     PLANNED vs ACTUAL
               |
               v
      DELAY / RISK / IMPACT
               |
               v
       MANAGEMENT ACTION
```

---

# 2. Problem Statement

## Existing Situation

Infrastructure projects involve multiple disciplines executing work in parallel, including:

- Civil
- Piping
- Static Equipment
- Rotating Equipment
- Electrical
- Instrumentation
- HSE
- Contractors and subcontractors

The project schedule is normally structured and activity-oriented, while field execution information is often reported in natural language or semi-structured formats.

For example:

### Schedule

```text
PIP-104 — Erect Line 24 Spools
```

### Field Report

```text
Line 24 spool erection completed.
12 spools installed.
```

The two pieces of information are related, but the field report does not necessarily contain the exact schedule Activity ID.

## Problems Addressed

PROJECTSYNC AI addresses:

1. Fragmented field data
2. Terminology mismatch
3. Granularity mismatch
4. Manual reconciliation
5. Delayed schedule updates
6. Poor data quality
7. Limited trust in AI-generated updates
8. Weak traceability
9. Delayed identification of downstream impact
10. Loss of institutional execution knowledge

---

# 3. Proposed Solution

PROJECTSYNC AI creates a controlled bridge between project planning and field execution.

Instead of directly converting an AI interpretation into project truth, the platform follows a trust-aware pipeline:

```text
FIELD INFORMATION
       |
       v
AI INTERPRETATION
       |
       v
STRUCTURED EXECUTION EVENT
       |
       v
CANDIDATE ACTIVITIES
       |
       v
CONFIDENCE + EXPLANATION
       |
       v
RULE VALIDATION
       |
       v
HUMAN VERIFICATION WHEN REQUIRED
       |
       v
VERIFIED PROJECT RECORD
```

This architecture keeps AI responsible for understanding and interpretation while deterministic software controls calculations, dependencies, state transitions, permissions, and audit records.

---

# 4. Core Intelligence

PROJECTSYNC AI is designed around five questions.

| Question | System Response |
|---|---|
| What was planned? | Schedule / L5-L6 Activity |
| What actually happened? | DPR / Time Agent / Field Information |
| Where does it belong? | Activity Matching |
| Can we trust it? | Confidence + Rules + Evidence + Human Verification |
| What should the manager do now? | Progress + Impact + Delay + Risk + Action |

The system is therefore not only an AI extraction tool. It is an **execution intelligence and verification layer**.

---

# 5. End-to-End Workflow

## Complete Pipeline

```text
1. Import Project Schedule
          |
          v
2. Build L1-L6 Activity Hierarchy
          |
          v
3. Receive Field Report / DPR / Spreadsheet / Time Agent Input
          |
          v
4. Extract Structured Information
          |
          v
5. Normalize Terminology
          |
          v
6. Create Execution Event
          |
          v
7. Retrieve Candidate Activities
          |
          v
8. Semantic / Contextual Matching
          |
          v
9. Calculate Confidence
          |
          v
10. Generate Match Explanation
          |
          v
11. Apply Deterministic Validation
          |
          +-----------------------------+
          |                             |
          v                             v
   High Confidence                Uncertain / Conflict
          |                             |
          v                             v
      Verification                 Review Queue
          |                             |
          +-------------+---------------+
                        |
                        v
                 Verified Progress
                        |
                        v
               Planned vs Actual
                        |
                        v
             Dependency Analysis
                        |
                        v
                Delay / Risk
                        |
                        v
                Manager Action
                        |
                        v
              Evidence + Audit
```

---

# 6. Key Features

## Schedule Intelligence

- Project management
- Schedule and activity management
- L1-L6 hierarchy
- Activity dependencies
- Planned dates
- Planned quantities
- Schedule versions

## Field Data Intelligence

- DPR ingestion
- Spreadsheet ingestion
- Field updates
- Time Agent input
- Quantity capture
- Evidence attachments

## AI Intelligence

- Document understanding
- Information extraction
- Terminology normalization
- Execution Event generation
- L5/L6 activity matching
- Semantic similarity
- Confidence scoring
- Explainable match reasons

## Trust & Verification

- Rule validation
- Human verification
- Low-confidence review
- Unmatched events
- Conflict detection
- Duplicate detection
- Stale-data detection

## Project Control

- Verified progress
- Planned vs actual comparison
- Schedule variance
- Dependency impact
- Delay detection
- Risk identification
- Manager action workflows

## Traceability

- Evidence lineage
- Execution history
- Audit history
- Source-to-progress traceability
- Institutional execution memory

---

# 7. Schedule Hierarchy

PROJECTSYNC AI works with a six-level project schedule hierarchy.

```text
L1 — Project
 |
 +-- L2 — Area
       |
       +-- L3 — Discipline
             |
             +-- L4 — Work Package
                   |
                   +-- L5 — Activity
                         |
                         +-- L6 — Sub-Activity
```

| Level | Description |
|---|---|
| L1 | Project |
| L2 | Area |
| L3 | Discipline |
| L4 | Work Package |
| L5 | Activity |
| L6 | Sub-Activity |

The L5/L6 levels are particularly important because field execution must ultimately be connected to executable schedule activities.

---

# 8. Execution Event Model

The **Execution Event** is the central bridge between unstructured field information and structured project activities.

A field report such as:

```text
Line 24 spool erection completed.
12 spools installed today.
```

can be converted into an Execution Event:

```json
{
  "event_type": "SPOOL_ERECTION",
  "discipline": "PIPING",
  "line": "24",
  "quantity": 12,
  "unit": "SPOOLS",
  "event_date": "2026-09-18",
  "source": "DPR-1042"
}
```

The event can then be matched against schedule activities.

```text
Field Report
     |
     v
Execution Event
     |
     v
Candidate Retrieval
     |
     v
Activity Matching
     |
     v
Verified Progress
```

## Why Execution Events Matter

They provide a normalized intermediate representation between:

- Different field report formats
- Different terminology
- Different reporting granularity
- Different disciplines
- Structured schedule activities

This also allows:

```text
One Report
    |
    +----> Event A
    |
    +----> Event B
    |
    +----> Event C
```

and:

```text
Report A ----+
             |
Report B ----+----> Same Activity
             |
Report C ----+
```

---

# 9. AI Processing Architecture

The AI layer is divided into several responsibilities.

```text
                    AI LAYER
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
 Document         Information     Terminology
 Understanding   Extraction      Normalization
        |              |              |
        +--------------+--------------+
                       |
                       v
                Semantic Matching
                       |
                       v
                   Explanation
                       |
                       v
                 Time Agent
```

## Processing Pipeline

```text
Input
  |
  v
Pre-processing
  |
  v
Document / Text Extraction
  |
  v
Structured Field Extraction
  |
  v
Normalization
  |
  v
Execution Event
  |
  v
Candidate Retrieval
  |
  v
Semantic Matching
  |
  v
Confidence
  |
  v
Explanation
  |
  v
Rule Validation
  |
  v
Human Review if Required
```

## Candidate Matching Strategy

A prototype matching pipeline can use:

```text
Project Filter
      |
      v
Discipline Filter
      |
      v
Keyword / Metadata Retrieval
      |
      v
Vector / Semantic Similarity
      |
      v
LLM / Contextual Reasoning
      |
      v
Final Candidate Ranking
```

This reduces unnecessary AI calls and combines structured metadata with semantic understanding.

---

# 10. AI vs Deterministic Logic

PROJECTSYNC AI deliberately separates interpretation from critical calculations.

## AI Responsibilities

AI is responsible for:

- Document understanding
- Natural-language interpretation
- Information extraction
- Terminology normalization
- Semantic matching
- Match explanation
- Conversational Time Agent

## Deterministic Software Responsibilities

Normal application logic handles:

- Date arithmetic
- Quantity calculations
- Progress calculations
- Schedule variance
- Dependency calculations
- Thresholds
- State transitions
- Permissions
- Audit records
- Database updates

This separation improves predictability, traceability, and control.

---

# 11. Confidence & Explainability

The system should not only answer:

> "Which activity does this report match?"

It should also answer:

> "Why did the system choose this activity?"

Example:

```text
Activity:
PIP-104 — Erect Line 24 Spools

AI Match:
94%

Reasons:
✓ Line number matches
✓ Discipline matches
✓ Event type matches
✓ Location matches
✓ Terminology similarity
```

## Confidence-Based Routing

A prototype can use configurable confidence thresholds.

```text
90%+       → High Confidence → Verification / Auto-processing policy
70–89%     → Medium Confidence → Human Review
<70%       → Low Confidence → Unmatched / Review
```

Thresholds should remain configurable rather than being hard-coded into the product concept.

---

# 12. Human-in-the-Loop Verification

AI interpretation is treated as a suggestion rather than unquestionable project truth.

```text
AI Suggestion
      |
      v
Confidence
      |
      v
Explanation
      |
      v
Rule Validation
      |
      +------------------+
      |                  |
      v                  v
High Confidence      Uncertain
      |                  |
      v                  v
 Verification        Human Review
                         |
              +----------+----------+
              |          |          |
              v          v          v
           Approve     Change     Reject
              |
              v
      Verified Record
```

The planner can:

- Approve a match
- Change the mapped activity
- Correct extracted fields
- Reject the result
- Resolve conflicts
- Mark an event unmatched
- Provide feedback

---

# 13. Exception Center

The Exception Center focuses human attention on cases that cannot safely be processed automatically.

## Exception Types

```text
+----------------------+
| EXCEPTION CENTER     |
+----------------------+
| Low Confidence       |
| Unmatched            |
| Conflicting          |
| Duplicate            |
| Missing Evidence     |
| Stale Data           |
+----------------------+
```

## Review Actions

- Approve
- Reject
- Change activity
- Correct extracted information
- Resolve conflict
- Mark unmatched
- Create or associate a new record where permitted

The goal is to make uncertainty visible rather than hiding it.

---

# 14. Progress & Schedule Intelligence

After verification, execution information can update project progress.

## Progress Sources

Progress can be calculated using:

- Quantity-based progress
- Activity/milestone completion
- Explicit percentage reported by the field
- Other configured project rules

The method used should remain visible to users.

## Planned vs Actual

Example:

```text
Activity:
PIP-104 — Erect Line 24 Spools

Planned Progress: 90%
Actual Progress: 65%

Variance:
-25 percentage points

Status:
DELAYED
```

The system can also track:

- Planned start
- Planned finish
- Actual start
- Actual finish
- Actual quantity
- Remaining quantity
- Progress percentage
- Schedule variance

---

# 15. Dependency & Risk Intelligence

A local delay may affect downstream activities.

Example:

```text
Spool Fabrication
        |
        v
Line 24 Erection
        |
        v
Welding
        |
        v
Hydro Testing
        |
        v
Commissioning
```

If Line 24 Erection is delayed, the system can identify downstream activities that may be affected.

## Delay Rules

Examples include:

```text
Actual Finish > Planned Finish
        ↓
Delayed
```

```text
Actual Progress < Expected Progress
        ↓
At Risk
```

```text
Milestone Deadline Passed
AND
Completion < 100%
        ↓
Critical
```

```text
Delayed Predecessor
        ↓
Downstream Dependency Risk
```

---

# 16. Evidence & Auditability

Every important progress update should be traceable to its source.

```text
Activity
   |
   v
Actual Progress
   |
   v
Execution Event
   |
   v
Field Report
   |
   v
Evidence
   |
   v
Audit Record
```

Example:

```text
Activity:
PIP-104

Progress:
65% → 80%

Source:
DPR-1042

Execution Event:
12 spools installed

AI Match:
94%

Verification:
Human verified

Timestamp:
2026-09-18
```

## Audit Information

An audit record should be able to identify:

- Who made the change
- What changed
- Previous value
- New value
- When it changed
- Source of information
- Approval / verification status

---

# 17. Time Agent

The Time Agent provides a lightweight field interface for recording execution information.

Example:

```text
User:
"Started Line 24 erection at 9:30 AM."

        |
        v

AI Interpretation

Activity:
PIP-104

Event:
Start

Time:
09:30 AM

Confidence:
94%

        |
        v

[ CONFIRM ]
```

The Time Agent is intended to reduce the effort required for field personnel to record execution information.

Primary action:

```text
+ Submit Field Update
```

---

# 18. User Roles

## Project Manager

Needs visibility into:

- Overall progress
- Planned vs actual
- Delayed activities
- At-risk activities
- Pending reviews
- Discipline performance
- Downstream impact
- Evidence
- Required actions

## Site Engineer / Supervisor

Can:

- View assigned activities
- Submit field updates
- Upload DPRs
- Record start/end events
- Add quantities
- Attach evidence
- Respond to review requests

## Planner / Planning Engineer

Reviews:

- Activity matches
- Unmatched events
- Conflicts
- Duplicate records
- Low-confidence matches
- Schedule-impact information

Can:

- Approve
- Reject
- Correct mappings
- Correct extracted fields
- Resolve conflicts
- Mark records appropriately
- Provide feedback

## Administrator

Manages:

- Users
- Roles
- Projects
- Permissions
- System configuration
- AI thresholds
- Audit logs
- Integrations
- Project membership

---

# 19. System Architecture

```text
                         PROJECTSYNC AI
                               |
        +----------------------+----------------------+
        |                                             |
        v                                             v
  WEB / USER LAYER                              FIELD LAYER
        |                                             |
        |                                      DPR / Reports
        |                                      Spreadsheet
        |                                      Time Agent
        |                                             |
        +----------------------+----------------------+
                               |
                               v
                         API / BACKEND
                               |
             +-----------------+-----------------+
             |                                   |
             v                                   v
       AI PROCESSING                       BUSINESS LOGIC
             |                                   |
      +------+------+                    +-------+-------+
      |      |      |                    |       |       |
      v      v      v                    v       v       v
  Extract Normalize Match             Progress Dependencies
                                      Variance  Audit
             |                                   |
             +----------------+------------------+
                              |
                              v
                         DATA LAYER
                              |
          +-------------------+-------------------+
          |                   |                   |
          v                   v                   v
      PostgreSQL         Object Storage       Vector Store
```

---

# 20. Technology Stack

## Frontend

- Next.js
- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- Recharts

## Backend

- Python
- FastAPI

## Database

- PostgreSQL
- pgvector

## AI

- Large Language Model
- Embeddings
- Semantic similarity
- Contextual reasoning

## Document Processing

- PyMuPDF
- pandas
- openpyxl
- OCR where required

## Infrastructure

- Docker
- Object storage / Supabase Storage
- Redis / background processing where required

> **Note:** Technologies should only be listed as implemented when they are actually present in the repository. Planned technologies should be marked as planned.

---

# 21. Database Model

The logical data model contains the following major entities:

```text
Organizations
     |
     +---- Users
     |
     +---- Projects
              |
              +---- Project Members
              |
              +---- Schedule Versions
              |         |
              |         +---- Activities
              |                  |
              |                  +---- Dependencies
              |
              +---- Field Reports
              |         |
              |         +---- Execution Events
              |                    |
              |                    +---- Matches
              |
              +---- Progress Updates
              |
              +---- Evidence
              |
              +---- Review Queue
              |
              +---- Risks
              |
              +---- Alerts
              |
              +---- Audit Logs
              |
              +---- Execution History
```

## Core Entities

- Organizations
- Users
- Roles
- Projects
- Project Members
- Schedule Versions
- Activities
- Dependencies
- Field Reports
- Execution Events
- Matches
- Progress Updates
- Evidence
- Review Queue
- Risks
- Alerts
- Audit Logs
- AI Runs
- AI Feedback
- Execution History

---

# 22. API Architecture

The backend can expose APIs such as:

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/auth/login` | Authenticate user |
| GET | `/projects` | List projects |
| POST | `/projects` | Create project |
| GET | `/projects/{id}/activities` | Get activities |
| POST | `/field-reports/upload` | Upload field report |
| POST | `/field-reports/{id}/process` | Process field report |
| POST | `/execution-events` | Create execution event |
| POST | `/matches/run` | Run activity matching |
| GET | `/review-queue` | Get review items |
| POST | `/review-queue/{id}/approve` | Approve match |
| POST | `/review-queue/{id}/reject` | Reject match |
| GET | `/activities/{id}/progress` | Get activity progress |
| GET | `/activities/{id}/evidence` | Get evidence |
| GET | `/projects/{id}/risks` | Get project risks |
| GET | `/projects/{id}/dashboard` | Get dashboard data |

## Example API Flow

```text
POST /field-reports/upload
        |
        v
Field Report Stored
        |
        v
POST /field-reports/{id}/process
        |
        v
Execution Event Generated
        |
        v
POST /matches/run
        |
        v
Candidate Activity
        |
        v
Confidence + Explanation
        |
        v
Review if Required
        |
        v
POST /review-queue/{id}/approve
        |
        v
Progress Update
        |
        v
Dashboard Refresh
```

---

# 23. Project Structure

A recommended repository organization is:

```text
PROJECTSYNC-AI/
│
├── frontend/
│   ├── app/
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── hooks/
│   ├── lib/
│   └── public/
│
├── backend/
│   ├── api/
│   ├── models/
│   ├── schemas/
│   ├── services/
│   ├── ai/
│   ├── matching/
│   ├── validation/
│   ├── database/
│   └── main.py
│
├── data/
│   ├── schedules/
│   ├── field-reports/
│   ├── evidence/
│   └── synthetic/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── matching/
│
├── docs/
│   ├── architecture/
│   ├── api/
│   └── diagrams/
│
├── .env.example
├── docker-compose.yml
├── requirements.txt
├── package.json
└── README.md
```

Adapt this structure to the actual repository.

---

# 24. Installation & Setup

## Prerequisites

Install:

- Git
- Node.js
- npm
- Python 3.x
- PostgreSQL
- Optional: Docker

Verify:

```bash
git --version
node --version
npm --version
python --version
```

---

## Clone Repository

```bash
git clone <REPOSITORY_URL>
cd <REPOSITORY_NAME>
```

---

## Frontend Setup

```bash
cd frontend
npm install
```

---

## Backend Setup

```bash
cd backend
python -m venv venv
```

### Windows

```bash
venv\Scripts\activate
```

### macOS / Linux

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# 25. Environment Variables

Create a `.env` file based on `.env.example`.

Example:

```env
DATABASE_URL=
AI_API_KEY=
SUPABASE_URL=
SUPABASE_ANON_KEY=
JWT_SECRET=
STORAGE_BUCKET=
```

Never commit:

```text
.env
```

to the repository.

Commit:

```text
.env.example
```

with placeholder values only.

---

# 26. Running the Application

## Start Backend

```bash
cd backend
uvicorn main:app --reload
```

The API will normally be available at:

```text
http://localhost:8000
```

If FastAPI documentation is enabled:

```text
http://localhost:8000/docs
```

## Start Frontend

In another terminal:

```bash
cd frontend
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:3000
```

> Use the actual ports and commands defined by the repository if they differ.

---

# 27. Demo Workflow

The recommended demonstration follows one complete field-to-schedule scenario.

## Step 1 — Load Schedule

Import a project schedule containing L1-L6 activities.

Example:

```text
PIP-104
Erect Line 24 Spools
Discipline: Piping
Planned Finish: 18 Sep 2026
```

## Step 2 — Submit Field Report

```text
Line 24 spool erection completed.
12 spools installed today.
```

## Step 3 — AI Extraction

The system extracts:

```text
Discipline: Piping
Line: 24
Event: Spool Erection
Quantity: 12
Date: 18 Sep 2026
```

## Step 4 — Execution Event

The extracted information becomes a structured Execution Event.

## Step 5 — Candidate Matching

The system searches schedule activities.

```text
PIP-104 — Erect Line 24 Spools
PIP-105 — Welding Line 24
PIP-106 — Hydro Testing
```

## Step 6 — Confidence

Example:

```text
PIP-104 → 94%
PIP-105 → 61%
PIP-106 → 43%
```

## Step 7 — Explanation

```text
✓ Line number matches
✓ Discipline matches
✓ Event type matches
✓ Location matches
✓ Semantic terminology matches
```

## Step 8 — Verification

High-confidence results can proceed according to configured policy.

Uncertain results enter the Review Queue.

## Step 9 — Progress Update

Verified execution updates activity progress.

## Step 10 — Impact Analysis

The system evaluates:

- Planned vs actual
- Schedule variance
- Dependencies
- Delay
- Risk
- Downstream impact

## Step 11 — Management Action

The manager can see:

```text
What happened?
        |
Where?
        |
Which activity?
        |
Can we trust it?
        |
What changed?
        |
What is affected?
        |
What should happen next?
```

---

# 28. Example Input & Output

## Input

```text
Line 24 spool erection completed.
12 spools installed today.
```

## Extracted Information

```json
{
  "discipline": "Piping",
  "line": "24",
  "event": "Spool Erection",
  "quantity": 12,
  "unit": "spools",
  "date": "2026-09-18"
}
```

## Execution Event

```json
{
  "event_type": "SPOOL_ERECTION",
  "discipline": "PIPING",
  "asset_reference": "LINE-24",
  "quantity": 12,
  "unit": "SPOOLS",
  "event_date": "2026-09-18"
}
```

## Match

```text
Activity:
PIP-104 — Erect Line 24 Spools

Confidence:
94%

Reasons:
- Line number match
- Discipline match
- Event type match
- Location compatibility
- Semantic similarity
```

## Verified Result

```text
Actual Quantity:
12 spools

Actual Progress:
Updated according to configured progress calculation

Source:
DPR-1042

Evidence:
Available / attached according to report

Audit:
Recorded
```

---

# 29. AI Safety Principles

PROJECTSYNC AI follows a trust-aware AI model.

The AI must not:

- Invent quantities
- Invent dates
- Invent activities
- Treat missing information as zero
- Silently resolve conflicts
- Delete evidence
- Directly overwrite critical records without appropriate controls
- Claim physical reality solely from text interpretation

## Missing Information

If information is absent, it should be represented as:

```text
UNKNOWN
```

or:

```text
NULL
```

rather than being guessed.

## Human Verification

When confidence is insufficient or information conflicts, the system should route the case to human review instead of forcing an activity match.

---

# 30. Testing

Testing should cover both normal operation and failure conditions.

## Functional Tests

- Authentication
- Role-based access
- Project creation
- Schedule import
- Activity creation
- DPR upload
- Spreadsheet ingestion
- AI extraction
- Execution Event creation
- Activity matching
- Confidence calculation
- Human verification
- Progress update
- Evidence attachment
- Audit creation

## AI / Matching Tests

- Normal reports
- Ambiguous reports
- Unmatched reports
- Low-confidence matches
- Terminology variation
- Missing fields
- Multiple activities with similar names
- Different reporting granularity

## Data Quality Tests

- Duplicate reports
- Conflicting reports
- Missing evidence
- Stale data
- Invalid dates
- Invalid quantities

## Schedule Intelligence Tests

- Planned vs actual
- Schedule variance
- Delayed activity
- At-risk activity
- Critical milestone
- Dependency impact

---

# 31. Dataset & Demonstration Data

For development and demonstration, the project can use synthetic or controlled project data.

Recommended disciplines include:

- Civil
- Piping
- Electrical
- Instrumentation
- Static Equipment
- Rotating Equipment

Recommended test cases include:

```text
Normal
Ambiguous
Unmatched
Delayed
Conflicting
Duplicate
Missing Information
Low Confidence
Dependency Impact
Stale Data
```

The demonstration data should not be presented as confidential operational data unless appropriate authorization exists.

---

# 32. MVP Scope

## Included in MVP

- Authentication
- Role-based access
- Project management
- Schedule/activity management
- DPR ingestion
- Spreadsheet ingestion
- Time Agent
- AI information extraction
- Execution Events
- Cross-discipline normalization
- L5/L6 activity matching
- Confidence scoring
- Explainable matching
- Rule validation
- Human verification
- Exception Center
- Progress updates
- Planned-vs-actual comparison
- Dependency analysis
- Delay detection
- Risk identification
- Evidence lineage
- Audit history
- Stale-data detection
- Manager dashboard
- Site Engineer workflow
- Institutional execution history
- Testing/benchmarking framework

---

# 33. Future Scope

The following capabilities are considered future extensions rather than core MVP requirements:

- Full CAD/DWG intelligence
- BIM/IFC integration
- Drone integration
- IoT sensor networks
- AR/VR
- Blockchain
- Full autonomous project management
- Universal Primavera integration
- Complex predictive forecasting
- Production-grade speech recognition
- Enterprise ERP replacement
- Fully autonomous schedule modification without controls

The product should prioritize the core planning-to-execution bridge before expanding into these areas.

---

# 34. Screens & Product Experience

## Manager Dashboard

Primary information:

```text
Overall Progress
Schedule Variance
Delayed Activities
At-Risk Activities
Pending Reviews
Stale Activities
Recent Execution Updates
```

## Field Report → AI

```text
Field Report
     |
     v
AI Extraction
     |
     v
Execution Event
     |
     v
Candidate Activities
     |
     v
Confidence
     |
     v
Explanation
```

## Review Queue

Displays:

- Low-confidence matches
- Unmatched events
- Conflicts
- Duplicate records
- Missing evidence

## Activity Intelligence

Displays:

- Activity status
- Planned progress
- Actual progress
- Planned dates
- Actual dates
- Variance
- AI match
- Evidence
- Dependencies
- Risks
- Audit history

## Site Engineer

Primary screens:

1. Home
2. Assigned Activities
3. Submit Update
4. Time Agent
5. My Reports
6. Evidence
7. Profile

Primary action:

```text
+ Submit Field Update
```

---

# 35. Project Differentiation

PROJECTSYNC AI is designed around the distinction between:

```text
AI-generated interpretation
          ≠
Project truth
```

Instead, the system creates a controlled chain:

```text
Field Data
    ↓
AI Interpretation
    ↓
Execution Event
    ↓
Candidate Activity
    ↓
Confidence
    ↓
Explanation
    ↓
Validation
    ↓
Human Verification
    ↓
Verified Progress
    ↓
Schedule Impact
    ↓
Action
```

This provides:

- Traceability
- Explainability
- Human control
- Evidence lineage
- Exception handling
- Schedule awareness
- Dependency intelligence

The product is positioned as an **intelligent execution-data layer**, rather than a replacement for existing project scheduling systems.

---

# 36. Limitations

PROJECTSYNC AI has several important limitations.

## AI Limitations

AI interpretation may be uncertain when:

- Field descriptions are incomplete
- Activity names are highly similar
- Location information is missing
- Quantities are ambiguous
- Multiple activities can explain the same report
- Reports contain contradictory information

## Data Limitations

System accuracy depends on:

- Schedule quality
- Field-report quality
- Activity metadata
- Discipline information
- Location/asset identifiers
- Evidence availability

## Operational Limitation

AI should not be treated as an autonomous authority over physical project reality.

Human verification and deterministic controls remain important for critical project updates.

---

# 37. Team

## Team-VernoNix

### Project

**PROJECTSYNC AI**

### SIH

**Smart India Hackathon 2026**

### Problem ID

**SIH26122**

### Organization

**Oil India Limited**

### Contributions

Team responsibilities may include:

- Product architecture
- AI / ML
- Backend engineering
- Frontend engineering
- Database engineering
- UI/UX
- Research
- Documentation
- Testing
- Deployment

---

# 38. License

This project is developed as part of **Smart India Hackathon 2026**.

If this repository is released under a specific open-source license, replace this section with the applicable license and include the corresponding `LICENSE` file.

---

# Project Vision

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
