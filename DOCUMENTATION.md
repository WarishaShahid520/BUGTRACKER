# BugTrack – Project Documentation

## 1. Overview
BugTrack lets software teams report, track, update, test and resolve defects. It is a client-side single-page app; all data lives in Local Storage under the key `bugtrack.issues.v1`.

## 2. Functional Requirements
| ID | Requirement |
|----|-------------|
| FR1 | Create an issue with all fields and an auto-generated ID |
| FR2 | Edit and delete issues |
| FR3 | Status changes follow the defect lifecycle rules |
| FR4 | Search by ID or title; filter by severity, priority, status |
| FR5 | Each issue has a test checklist, result and Pass/Fail status |
| FR6 | Dashboard and analytics update in real time |
| FR7 | Data persists in Local Storage |

Non-functional: responsive layout, dark mode, no external dependencies, fast load.

## 3. Use Cases
| ID | Name | Actor | Summary |
|----|------|-------|---------|
| UC1 | Report Bug | Reporter | Fill form; system assigns ID, status Open |
| UC2 | Triage Issue | Lead | Set severity/priority; move to In Progress |
| UC3 | Hand Over Fix | Developer | Move to Testing |
| UC4 | Verify Fix | QA | Run checklist; Pass → Resolved, Fail → In Progress |
| UC5 | Close Issue | Lead | Close Resolved issue or reopen on regression |

## 4. Defect Lifecycle
Open → In Progress → Testing → Resolved → Closed, with loops back for failed tests and reopened defects.

## 5. State Transitions
| From | Allowed next states |
|------|---------------------|
| Open | In Progress, Closed |
| In Progress | Open, Testing |
| Testing | In Progress, Resolved |
| Resolved | Closed, Open |
| Closed | Open |

## 6. Data Model
`Issue { id, title, desc, reporter, module, steps, expected, actual, severity, priority, status, created, test: { checklist[{t,done}], result, status } }`

## 7. Test Cases
| ID | Test | Expected |
|----|------|----------|
| TC01 | Create issue with all fields | Saved with next ID, status Open |
| TC02 | Submit with empty title | Validation blocks submit |
| TC03 | Edit title | Change persists after reload |
| TC04 | Delete issue | Removed from list and dashboard |
| TC05 | Move Open → Resolved | Not offered in the dropdown |
| TC06 | Search “BUG-003” | Only that issue shown |
| TC07 | Filter Critical + Open | Both filters applied |
| TC08 | Tick checklist, set Pass | Saved, shown in Issues table |
| TC09 | Toggle dark mode, reload | Theme persists |
| TC10 | 375px viewport | Layout stacks, no horizontal scroll |
