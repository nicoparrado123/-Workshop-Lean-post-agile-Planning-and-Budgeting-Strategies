# High-Level Architecture Document
## Municipal Citizen Request & Complaint Management Platform

---

## System Metaphor

> **"A digital city hall that never closes"** — Citizens walk in through any door (web/mobile), submit their request at the front desk (API Gateway), it gets routed to the right department (microservices), and they can check the status board at any time (real-time tracking).

---

## Architecture Diagram (Text-Based)

```
┌─────────────────────────────────────────────────────────────────┐
│                        CITIZENS / ADMINS                        │
│              (Web Browser / Mobile Browser)                     │
└───────────────────────────┬─────────────────────────────────────┘
                            │ HTTPS
┌───────────────────────────▼─────────────────────────────────────┐
│                      FRONTEND LAYER                             │
│                                                                 │
│   ┌─────────────────────┐     ┌─────────────────────────────┐  │
│   │  Citizen Portal     │     │  Admin Dashboard            │  │
│   │  - Submit requests  │     │  - Assign to departments    │  │
│   │  - Track status     │     │  - Monitor SLAs             │  │
│   │  - Messaging        │     │  - Generate reports         │  │
│   └─────────────────────┘     └─────────────────────────────┘  │
│                    React.js / Next.js (SPA)                     │
└───────────────────────────┬─────────────────────────────────────┘
                            │ REST / WebSocket
┌───────────────────────────▼─────────────────────────────────────┐
│                      API GATEWAY                                │
│              (Authentication · Rate Limiting · Routing)         │
└──────┬──────────────┬──────────────┬──────────────┬────────────┘
       │              │              │              │
┌──────▼──────┐ ┌─────▼──────┐ ┌────▼──────┐ ┌────▼──────────┐
│  Request    │ │  User &    │ │ Messaging │ │  Reporting    │
│  Service   │ │  Auth      │ │  Service  │ │  Service      │
│             │ │  Service   │ │           │ │               │
│ - Create   │ │ - Register │ │ - Inbox   │ │ - KPIs        │
│ - Assign   │ │ - Login    │ │ - Notify  │ │ - SLA reports │
│ - Update   │ │ - Roles    │ │ - History │ │ - Exports     │
│ - Close    │ │            │ │           │ │               │
└──────┬──────┘ └─────┬──────┘ └────┬──────┘ └────┬──────────┘
       │              │              │              │
┌──────▼──────────────▼──────────────▼──────────────▼──────────┐
│                      DATABASE LAYER                            │
│                                                                │
│   ┌──────────────────────┐    ┌──────────────────────────┐   │
│   │  PostgreSQL           │    │  Redis (Cache)           │   │
│   │  - Users             │    │  - Sessions              │   │
│   │  - Requests          │    │  - Real-time status      │   │
│   │  - Departments       │    │  - Notifications queue   │   │
│   │  - Audit logs        │    └──────────────────────────┘   │
│   └──────────────────────┘                                    │
└────────────────────────────────────────────────────────────────┘
       │              │              │
┌──────▼──────┐ ┌─────▼──────┐ ┌────▼──────────────────────────┐
│  Email/SMS  │ │  GIS /     │ │  Government Identity          │
│  Service    │ │  Maps API  │ │  Provider (SSO / OAuth2)      │
│  (Twilio /  │ │ (Google    │ │  (Existing public IT infra)   │
│   SendGrid) │ │  Maps)     │ │                               │
└─────────────┘ └────────────┘ └───────────────────────────────┘
```

---

## Architecture Explanation

### Frontend Layer
A **Single Page Application (SPA)** built with React.js/Next.js, split into two portals:
- **Citizen Portal**: submit requests with category, location, and photo attachments; track status in real time; exchange messages with the assigned department.
- **Admin Dashboard**: view all incoming requests, assign them to departments, set priorities, monitor SLA compliance, and export reports.

### API Gateway
Central entry point that handles **JWT authentication**, rate limiting, and routes traffic to the appropriate microservice. Enables future integration with other municipal systems without changing the frontend.

### Backend Microservices
Each service is independently deployable and owns its domain:

| Service | Responsibility |
|---------|---------------|
| Request Service | Full lifecycle of a citizen request (create → assign → resolve → close) |
| User & Auth Service | Registration, login, role management (citizen / admin / department head) |
| Messaging Service | Internal messaging thread per request, push/email notifications |
| Reporting Service | Aggregated KPIs, SLA breach alerts, CSV/PDF exports |

### Database Layer
- **PostgreSQL**: relational data (users, requests, departments, audit trail) — chosen for ACID compliance and government audit requirements.
- **Redis**: caching session tokens and real-time status updates via pub/sub.

### Third-Party Integrations
| Integration | Purpose |
|-------------|---------|
| SendGrid / Twilio | Email and SMS notifications to citizens |
| Google Maps API | Geolocate and display reported issues on a map |
| Government SSO (OAuth2) | Reuse existing public sector identity infrastructure |

### Scalability & Modularity Considerations
- Each microservice scales independently (e.g., Reporting can scale during month-end without affecting Request Service).
- Stateless services behind the API Gateway allow horizontal scaling.
- PostgreSQL read replicas for reporting queries to avoid impacting transactional workloads.
- Designed to run on-premise or on a government cloud (AWS GovCloud / Azure Government).
