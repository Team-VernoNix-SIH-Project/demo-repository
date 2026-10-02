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
## Schedule Twin
PlnEX provides a Plan vs Reality view for schedule activities.

| Planned | Actual |
|---|---|
| Planned Start | Actual Start |
| Planned Finish | Actual Finish |
| Planned Quantity | Actual Quantity |
| Planned Duration | Actual Duration |
The resulting variance gives project teams a direct view of what was planned versus what actually happened.

## Delay Impact Analysis
PlnEX can trace the downstream impact of delayed activities.
Example:
`Foundation Delay`
→ `Equipment Installation Delay`
→ `Piping Delay`
→ `Electrical Delay`
→ `Milestone Delay`
Instead of only identifying a delayed activity, the system helps explain how the delay propagates through project dependencies.

## Schedule Health
The platform can provide a transparent Schedule Health indicator based on measurable project signals such as:
- Schedule performance
- Milestone performance
- Progress variance
- Open risks
- Data quality
Each score can be broken down to show why the overall health changed.

## Data Quality
PlnEX monitors not only project progress but also the quality of the information used to calculate that progress.
Quality signals include:
- Completeness
- Timeliness
- Evidence coverage
- Schedule-linking coverage
- Consistency
This helps distinguish project progress from the reliability of the underlying progress information.

## Granularity Bridge
Field execution and project schedules may describe the same work at different levels of detail.
For example:
```text
Schedule Activity
Erect Line 24-XX
        │
        ├── Spool A
        ├── Spool B
        ├── Spool C
        └── Spool D
```
---

## What-if Simulator
Project managers can simulate schedule changes and inspect potential downstream effects.

Example:
```text
Foundation       +5 days
      ↓
Equipment        +3 days
      ↓
Piping           +3 days
      ↓
Final Milestone  +4 days
```


---

## Project Memory
Completed projects can contribute structured historical knowledge to future planning.
Project Memory can preserve:
- Delay causes
- Historical activity variance
- Activity duration patterns
- Dependency-related delays
- Execution history
- Recurring project issues
This turns completed-project information into reusable institutional knowledge rather than a static archive.

## Offline Field Workflow
Field updates can be designed for environments with limited connectivity.
The workflow is:
`Record → Store Locally → Capture Evidence → Connectivity Restored → Synchronize`
Field information can include:
- Progress updates
- Photos
- Timestamps
- Location information
This allows field execution data to be captured without requiring continuous network connectivity.

## One-Click Daily Update
The field workflow is designed to minimize manual data entry:
`Select Project → Select Task → Start / Complete → Add Evidence → Submit`
For conversational workflows, a short natural-language or voice update can also be converted into a structured execution event.

## Field Data Sources
PlnEX can support multiple forms of field execution input:
- Daily progress reports
- Spreadsheets
- Site diaries
- Scanned documents / PDFs
- Mobile field updates
- Conversational or voice input
These inputs are converted into structured execution events before being linked to schedule activities.

## Unmatched Execution Events
When an execution event cannot be reliably linked to an existing activity, PlnEX does not silently update the schedule.
The event can be routed to a review queue where the planner can:
- Select an existing activity
- Create a new activity
- Reject the event
- Leave it unmatched for later review

## Flexible Activity Mapping
PlnEX uses an intermediate execution-event layer so field execution does not have to map directly to exactly one schedule activity.
The model can support:
- One execution event → one activity
- Multiple execution events → one activity
- One execution event → multiple activities

This helps handle real-world differences between field-level reporting and schedule-level planning.

## Schedule Data Sources
Supported schedule inputs can include:
- Primavera exports
- MS Project exports
- Excel
- CSV
Imported schedules are normalized into a common activity structure containing information such as:
- Activity ID
- Activity Name
- WBS Level
- Discipline
- Planned Start
- Planned Finish
- Duration
- Predecessors
- Quantity
- Unit

## What Makes PlnEX Different
PlnEX is not simply a project-management dashboard.
Its core function is to connect:
`Unstructured Field Execution`
→ `Structured Execution Event`
→ `Schedule Activity`
→ `Verification`
→ `Actual Progress`
→ `Variance`
→ `Impact`
The dashboard is the visualization layer around this execution-to-schedule bridge.

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

### Core Idea
**PlnEX connects planned project schedules with real-world site execution by turning field reports into verified schedule updates and actionable project intelligence.**

This is the version I would use for the GitHub repository: **short enough to scan quickly, but complete enough for a judge, mentor, recruiter, or developer to understand the project.**

### Team
**Team VeryoNix**

