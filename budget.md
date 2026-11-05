# Development Budget Estimate
## Municipal Citizen Request & Complaint Management Platform

---

## Assumptions

- Sprint duration: **2 weeks**
- Team velocity: **35 story points / sprint** (conservative estimate for a new team)
- Total backlog: **137 story points** (full scope) / **77 points** (MVP)
- Rates are in **USD**, based on mid-level professionals in a Latin American public sector context
- Rates include salary + benefits overhead (~30%)
- Technology costs are monthly SaaS/cloud estimates

---

## Team Composition & Hourly Rates

| Role | # People | Hours/Sprint | Rate (USD/hr) | Cost/Sprint |
|------|----------|-------------|---------------|-------------|
| Project Manager (PM) | 1 | 80 | $35 | $2,800 |
| Frontend Developer | 2 | 80 each | $30 | $4,800 |
| Backend Developer | 2 | 80 each | $32 | $5,120 |
| QA Engineer | 1 | 80 | $25 | $2,000 |
| UX/UI Designer | 1 | 40 (part-time) | $28 | $1,120 |
| DevOps Engineer | 1 | 40 (part-time) | $35 | $1,400 |
| **Team Total** | **8** | | | **$17,240/sprint** |

---

## Technology Costs (Monthly)

| Service | Purpose | Cost/Month |
|---------|---------|-----------|
| Cloud Hosting (AWS / Azure Gov) | App servers, DB, Redis | $400 |
| SendGrid | Email notifications | $20 |
| Twilio | SMS notifications | $50 |
| Google Maps API | Geolocation | $30 |
| CI/CD & Monitoring tools | GitHub Actions, Datadog | $60 |
| **Tech Total** | | **$560/month** |

Tech cost per sprint (2 weeks) ≈ **$280**

---

## Sprint & Budget Calculation

### Full Scope (137 story points)

```
Sprints needed = 137 ÷ 35 = ~4 sprints (rounded up)
                                        ↑ conservative: use 5 sprints for buffer

Cost per sprint = $17,240 (team) + $280 (tech) = $17,520
Total budget    = $17,520 × 5 sprints = $87,600
```

### MVP Only (77 story points — Epics 1–4)

```
Sprints needed = 77 ÷ 35 = ~3 sprints (rounded up)

Total budget   = $17,520 × 3 sprints = $52,560
```

---

## Budget Summary Table

| Scenario | Sprints | Team Cost | Tech Cost | **Total** |
|----------|---------|-----------|-----------|-----------|
| MVP (Epics 1–4) | 3 | $51,720 | $840 | **$52,560** |
| Full Scope | 5 | $86,200 | $1,400 | **$87,600** |
| Full Scope + 20% risk buffer | 5 | — | — | **~$105,120** |

---

## Budget Range

| | Low Estimate | High Estimate |
|-|-------------|--------------|
| MVP | $48,000 | $60,000 |
| Full Platform | $85,000 | $110,000 |

> Range accounts for: team ramp-up time, government procurement delays, scope changes, and integration complexity with existing public IT infrastructure.

---

## Notes for Fixed-Budget Scenarios

If the municipality sets a **fixed budget** (e.g., $60,000):
- Prioritize **Must Have** epics (1–4) first → MVP delivered within budget
- Defer Reporting (Epic 6) and Map (Epic 7) to a Phase 2 contract
- Use velocity reviews after Sprint 1 to re-forecast remaining capacity

If the municipality sets a **fixed scope**:
- Lock the backlog at 137 points
- Derive cost from velocity and team rates as shown above
- Add a 20% contingency buffer for public sector projects
