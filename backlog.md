# Agile Product Backlog
## Municipal Citizen Request & Complaint Management Platform

Estimation scale (Fibonacci): 1 · 2 · 3 · 5 · 8 · 13

---

## User Story Map

```
CITIZEN JOURNEY:    Register → Submit Request → Track Status → Communicate
ADMIN JOURNEY:      Login    → Assign Request → Monitor SLAs → Report
```

---

## Epic 1 — User Management & Authentication
*Priority: 🔴 Must Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-01 | As a citizen, I want to register with my email so I can submit requests. | 3 |
| US-02 | As a citizen, I want to log in securely so my data is protected. | 3 |
| US-03 | As an admin, I want to log in via the government SSO so I don't need a separate account. | 8 |
| US-04 | As an admin, I want to assign roles (citizen / department staff / admin) so access is controlled. | 5 |
| US-05 | As a citizen, I want to reset my password via email so I can recover access. | 3 |

**Epic Total: 22 points**

---

## Epic 2 — Citizen Request Submission
*Priority: 🔴 Must Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-06 | As a citizen, I want to select a request category (lighting, waste, infrastructure) so it reaches the right department. | 3 |
| US-07 | As a citizen, I want to describe my issue and attach a photo so the department understands the problem. | 5 |
| US-08 | As a citizen, I want to pin the location on a map so the team knows exactly where the issue is. | 8 |
| US-09 | As a citizen, I want to receive a confirmation email with a tracking number after submitting. | 3 |
| US-10 | As a citizen, I want to submit a request without an account (guest mode) so the process is accessible to everyone. | 5 |

**Epic Total: 24 points**

---

## Epic 3 — Request Tracking & Status Updates
*Priority: 🔴 Must Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-11 | As a citizen, I want to see the current status of my request (Received / In Progress / Resolved) so I know what's happening. | 3 |
| US-12 | As a citizen, I want to receive an SMS/email notification when my request status changes. | 5 |
| US-13 | As a citizen, I want to view the full history of status changes for my request. | 3 |
| US-14 | As an admin, I want to update the status of a request so citizens are kept informed. | 2 |

**Epic Total: 13 points**

---

## Epic 4 — Admin Request Management
*Priority: 🔴 Must Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-15 | As an admin, I want to see all incoming requests in a dashboard so I can manage the workload. | 5 |
| US-16 | As an admin, I want to assign a request to a department so the right team handles it. | 3 |
| US-17 | As an admin, I want to set a priority level (low / medium / high / urgent) for each request. | 2 |
| US-18 | As an admin, I want to filter requests by category, status, and department so I can focus on what matters. | 5 |
| US-19 | As a department staff member, I want to see only the requests assigned to my department. | 3 |

**Epic Total: 18 points**

---

## Epic 5 — Messaging & Communication
*Priority: 🟡 Should Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-20 | As a citizen, I want to send a message to the department handling my request so I can provide more details. | 5 |
| US-21 | As a department staff member, I want to reply to a citizen's message so I can request clarification. | 5 |
| US-22 | As a citizen, I want to receive a notification when I get a reply so I don't miss updates. | 3 |

**Epic Total: 13 points**

---

## Epic 6 — Reporting & Analytics
*Priority: 🟡 Should Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-23 | As an admin, I want to see average resolution time per department so I can identify bottlenecks. | 8 |
| US-24 | As an admin, I want to see the number of requests by category and month so I can spot trends. | 5 |
| US-25 | As an admin, I want to export a report as CSV or PDF so I can share it with city council. | 5 |
| US-26 | As an admin, I want to receive an alert when a request exceeds its SLA deadline. | 8 |

**Epic Total: 26 points**

---

## Epic 7 — Map & Geolocation View
*Priority: 🟢 Nice to Have*

| ID | User Story | Points |
|----|-----------|--------|
| US-27 | As an admin, I want to see all open requests plotted on a city map so I can identify hotspots. | 13 |
| US-28 | As a citizen, I want to see nearby reported issues on a map so I avoid duplicating requests. | 8 |

**Epic Total: 21 points**

---

## Backlog Summary

| Epic | Priority | Story Points |
|------|----------|-------------|
| 1 – User Management & Auth | 🔴 Must Have | 22 |
| 2 – Request Submission | 🔴 Must Have | 24 |
| 3 – Request Tracking | 🔴 Must Have | 13 |
| 4 – Admin Management | 🔴 Must Have | 18 |
| 5 – Messaging | 🟡 Should Have | 13 |
| 6 – Reporting & Analytics | 🟡 Should Have | 26 |
| 7 – Map & Geolocation | 🟢 Nice to Have | 21 |
| **TOTAL** | | **137 points** |

---

## MVP Scope (Must Have only)
**77 story points** → Epics 1–4
