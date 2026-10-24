# 🐞 BugTrack – Software Issue Tracking System

A SaaS-style bug and issue tracker built with **HTML, CSS and vanilla JavaScript**. Data is stored in the browser via **Local Storage**, so no backend or install is needed.

## Features
- Dashboard: total, open, in-progress, resolved and critical counts
- Issue CRUD with auto-generated IDs (BUG-001…), full bug-report fields
- Severity (Low–Critical), Priority (Low–Urgent) and a 5-state workflow with enforced transitions
- Search by ID or title; filter by severity, priority and status
- Testing module: checklist, test result, Pass/Fail per issue
- Analytics: resolution rate, open vs closed, severity and status distribution
- Built-in SE docs: requirements, use cases, defect lifecycle, state transitions, test cases
- Dark mode, glassmorphism, responsive layout, animations

## Run
Open `index.html` in any modern browser. Sample data loads on first run. To reset, clear this site’s Local Storage.

## Structure
```
bugtrack/
├── index.html
├── css/style.css
├── js/data.js        # sample data + SE documentation content
├── js/app.js         # state, rendering, CRUD, filters, testing, analytics
├── docs/DOCUMENTATION.md
└── README.md
```

## Status workflow
Open → In Progress → Testing → Resolved → Closed. Reopening is allowed (Resolved/Closed → Open; Testing → In Progress). See `docs/DOCUMENTATION.md`.

## Future improvements
User accounts and roles, comments and attachments, backend API with a database, CSV export, assignee field.
