# PlnEX — Planning-to-Execution Bridge

> AI-powered infrastructure project progress tracking and schedule-linking platform.
> 
![SIH 2026](https://img.shields.io/badge/Smart%20India%20Hackathon-2026-blue)
![SIH26122](https://img.shields.io/badge/Problem%20Statement-SIH26122-orange)
![Oil India Limited](https://img.shields.io/badge/Sponsor-Oil%20India%20Limited-success)
![Status](https://img.shields.io/badge/Status-Prototype-yellow)

## About
PlnEX is our solution for **Smart India Hackathon 2026 — SIH26122**, sponsored by **Oil India Limited**.
The idea is simple: connect the **project schedule** with what is actually happening at the construction site.
Project schedules contain structured information such as activities, dates, quantities and dependencies. Field teams, on the other hand, provide progress through daily reports, PDFs, spreadsheets and supervisor updates.

PlnEX connects these two sources using AI.
---

## How It Works
```text
PROJECT SCHEDULE
       ↓
L1–L6 ACTIVITY TREE
       ↓
FIELD REPORT
       ↓
AI EXTRACTION
       ↓
EXECUTION EVENT
       ↓
ACTIVITY MATCHING
       ↓
CONFIDENCE SCORE
       ↓
HUMAN REVIEW / AUTO APPROVAL
       ↓
VERIFIED PROGRESS
       ↓
PLANNED vs ACTUAL
       ↓
DELAY & RISK
       ↓
EVIDENCE + AUDIT
       ↓
DASHBOARD
```

## L1–L6 Structure
PlnEX uses a six-level project hierarchy:
```text
L1 Project
 └── L2 Area
      └── L3 Discipline
           └── L4 Work Package
                └── L5 Activity
                     └── L6 Sub-Activity
```

### Example:
A supervisor submits:
```
Line 24 spool erection completed.
12 spools installed today.
```
PlnEX extracts:
```
Discipline : Piping
Line       : 24
Event      : Spool Erection
Status     : Completed
Quantity   : 12
```
It then compares the report with schedule activities:
```
PIP001 — Erect Line 24       94%
PIP002 — Weld Line 24        51%
PIP003 — Hydro Test Line 24  18%
```
The system can also explain the match:
```
✓ Line number matched
✓ Discipline matched
✓ Event type matched
✓ Activity wording matched
✓ Date compatible
```

### Confidence & Human Review
PlnEX does not blindly accept every AI result.
```
≥90%     → Auto Approve
70–89%   → Human Review
<70%     → Unmatched
```
For uncertain results, the planner can:
* Approve
* Change the activity
* Reject
* Mark as unmatched
This keeps the human planner in control.

### Progress & Risk
After a match is verified, the system can update:
* Actual start
* Actual finish
* Actual quantity
* Progress %
It then compares planned and actual execution.
```
Planned Finish : 15 Sept
Actual Finish  : 17 Sept
Variance       : +2 Days`
```
PlnEX can identify:
* Delayed activities
* At-risk activities
* Critical milestones
* Dependency risks
* Stale information
* Conflicting reports
* Duplicate reports

### Evidence & Audit
Every important progress update can be connected back to its source:
```
Activity
   ↓
Progress Update
   ↓
Field Report
   ↓
Evidence
```
The audit trail records important changes such as:
* Previous value
* New value
* Source report
* Timestamp
* User
* Approval status
* AI confidence

### Key Features
* Schedule import from Excel/CSV
* L1–L6 activity hierarchy
* Field report ingestion
* AI information extraction
* AI schedule activity matching
* Explainable confidence scores
* Human review queue
* Unmatched report handling
* Actual progress tracking
* Planned vs actual comparison
* Delay detection
* Dependency analysis
* Evidence-linked progress
* Audit history
* Data quality monitoring
* Conflict and duplicate detection
* CAD/drawing progress visualization

## Technology Stack
### Frontend
* Next.js
* React
* Tailwind CSS
* shadcn/ui
### Backend & Database
* Supabase
* PostgreSQL
* Supabase Storage
### AI
* Gemini API
### Visualization
* Recharts
### Deployment
* Vercel
### Architecture
```
Excel / CSV Schedule
        │
        ▼
 Schedule Engine
        │
        ▼
   L1–L6 Activities
        │
        │
Field Reports ──→ AI Extraction
                       │
                       ▼
                Execution Event
                       │
                       ▼
                Activity Matching
                       │
                       ▼
                Confidence Score
                       │
              ┌────────┼────────┐
              ▼        ▼        ▼
             Auto    Review   Unmatched
              │        │        │
              └────────┼────────┘
                       ▼
                Verified Progress
                       │
                       ▼
                 Risk Analysis
                       │
                       ▼
              Evidence + Audit
                       │
                       ▼
                   Dashboard
```

## AI vs Application Logic
### AI handles
* Understanding field reports
* Information extraction
* Semantic activity matching
* Match explanations
* Natural-language explanations
### Application logic handles
* Date calculations
* Progress calculations
* Variance
* Dependency calculations
* Delay rules
* Database updates
* Audit records

### Project Status
PlnEX is being developed as a **Smart India Hackathon 2026 prototype.**
Our main focus is to make the complete workflow reliable:
```
SCHEDULE
   ↓
FIELD REPORT
   ↓
AI EXTRACTION
   ↓
L5/L6 MATCH
   ↓
CONFIDENCE
   ↓
HUMAN VALIDATION
   ↓
PROGRESS UPDATE
   ↓
DELAY / RISK
   ↓
EVIDENCE
   ↓
DASHBOARD
```

### Team
**Team VeryoNix**

**Smart India Hackathon 2026**

**Problem Statement:** SIH26122

**Sponsor:** Oil India Limited

**Track:** Software

**Theme:** Smart Automation

### Core Idea
**PlnEX connects planned project schedules with real-world site execution by turning field reports into verified schedule updates and actionable project intelligence.**

This is the version I would use for the GitHub repository: **short enough to scan quickly, but complete enough for a judge, mentor, recruiter, or developer to understand the project.**
 
