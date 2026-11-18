# DineDash
## Two-Member Project Work Plan

**Project:** Demand-Aware Canteen Ordering and Real-Time Token Dispatch System  
**Purpose:** A practical 15-week division of work for two teammates. This document defines ownership, shared responsibilities, integration points, GitHub workflow and review milestones. Replace “Member 1” and “Member 2” with the team members’ names.

> **Faculty approval check:** The ADS481 Student Guide states that each team has 3 members. This document allocates the work for your requested 2-person team, but confirm with your faculty guide that a 2-member team is permitted before treating this allocation as final.

## 1. Project goal

DineDash aims to reduce congestion in the college canteen by digitising order flow between students, the billing point and food counters. It supports walk-in orders through a billing interface and, after the core workflow is stable, advance orders through capacity-controlled pickup slots. Paid orders are converted into digital tokens and counter-specific tickets; staff update preparation status and students collect food when ready.

## 2. The two-person ownership model

| Member | Primary ownership | Main deliverables |
|---|---|---|
| **Member 1 — Backend & Data** | Java/Spring Boot backend, database, order rules and concurrency | REST API, PostgreSQL schema/migrations, payment confirmation flow, token and ticket dispatch, slot-capacity transactions, backend tests and event logging. |
| **Member 2 — Frontend & Analytics** | React application, user interfaces, API integration and analytics | Student/billing/counter/admin screens, live status UI, API integration, analytics dashboard, Python analysis and visualisations. |

## 3. Work both members must share

- Agree on the final workflow and requirements before implementation; validate actual counter arrangements with canteen staff.
- Collect baseline observations of the current queues and service times, subject to college/canteen permission.
- Create and review the architecture, ER diagram, class diagram and API contract together.
- Integrate modules regularly, test the complete end-to-end workflow and fix cross-module defects together.
- Contribute to literature survey, report, presentation, demonstration and viva preparation.

## 4. Detailed responsibility split

### Member 1 — Backend, database and operating-systems implementation

1. Create the Spring Boot project and organise the backend as a modular monolith (one application with clearly separated modules).
2. Design and maintain PostgreSQL tables, relationships, keys, constraints, indexes and versioned database migrations.
3. Implement core domain logic: menu items, orders, order items, payments, counters, counter tickets, tokens and order-status transitions.
4. Build REST endpoints and document request/response formats in the shared API contract.
5. Implement walk-in order entry and staff-confirmed cash/UPI payment recording. Use a mock payment flow for online pre-orders; do not depend on a real payment gateway.
6. Generate unique tokens and split multi-counter orders into counter-specific tickets while keeping one parent order.
7. Implement dispatch and concurrency features: dispatcher/executor threads, bounded queues where appropriate, synchronisation, safe slot booking, idempotency and atomic token redemption.
8. Publish order events and timestamps needed for live updates and analytics; provide reliable database-backed recovery after a server restart.
9. Write backend unit/integration tests, concurrency tests and basic load tests; maintain backend setup instructions.

### Member 2 — Frontend, integration and analytics

1. Create one React application with role-based screens for students, billing staff, food-counter staff and administrators.
2. Build the student menu, cart, checkout, pickup-slot selection, token view and order-tracking experience.
3. Build the billing/POS screen for staff to enter walk-in orders, confirm recorded payments and issue a token/printable slip.
4. Build the counter dashboard showing queued, preparing and ready tickets, with actions to update status and verify collection.
5. Build the admin screens for menu/counter configuration and operational reporting.
6. Integrate each screen with the backend using the agreed REST API contract; handle loading, errors, invalid/expired slots and unavailable items.
7. Implement WebSocket client updates for live order status. Add REST refresh/polling fallback when the connection drops.
8. Create the analytics dashboard and Python workflow to clean event/order data, calculate waiting-time and counter metrics, and produce charts.
9. Write frontend component/integration tests, document how to run the UI and check usability with a small number of test users.

### Shared ownership boundaries

| Area | Owner | Other member contributes |
|---|---|---|
| Database schema and migrations | Member 1 | Review data needs and test queries. |
| API contract | Both | Agree before either side builds against it. |
| React screens and UI components | Member 2 | Review workflows and test with API. |
| Business rules and concurrency | Member 1 | Verify behaviour through UI and test cases. |
| Event data and analytics | Member 2 (analysis); Member 1 (event capture) | Agree on event names and timestamps. |

## 5. Fifteen-week execution roadmap

The roadmap follows the ADS481 guide’s approximate 15-week schedule. The department’s announced dates and faculty guide instructions take priority. Review 1 is targeted around Week 5 and Review 2 around Week 9.

| Week | Milestone | Member 1 — Backend/Data | Member 2 — Frontend/Analytics | Exit result |
|---:|---|---|---|---|
| 1 | Approval, observation and scope | Backend requirements, order states and data to capture. | Map student/staff journeys; record queue observation sheet. | Approved problem scope and initial field notes. |
| 2 | Baseline and research | Identify service metrics; draft database entities and risks. | Collect timing observations; review 2–3 related systems/papers. | Baseline dataset, literature notes and requirements draft. |
| 3 | System design | ER model, class model, module boundaries and API draft. | Wireframes, role journeys and screen list; review API draft. | Architecture, ER/class diagrams and agreed API contract. |
| 4 | Development setup | Create Spring Boot skeleton, PostgreSQL connection and migrations. | Create React/Vite skeleton, routes and shared layout. | Both applications run locally; repository conventions agreed. |
| 5 | Review 1 preparation | Demonstrate design, schema and first backend endpoints. | Demonstrate wireframes/prototype and requirements. | Review 1 package: problem, objectives, architecture, diagrams and progress. |
| 6 | Walk-in ordering core | Implement menu/order creation, payment record and token generation. | Build billing/POS and student menu/cart screens against API. | A walk-in order can be entered and saved. |
| 7 | Counter ticket dispatch | Split orders into counter tickets; implement status rules and dispatch. | Build counter dashboard and connect order/ticket APIs. | Paid order appears at the correct counter dashboard. |
| 8 | Collection and MVP hardening | Implement QR/token validation, duplicate protection and backend tests. | Build token display, ready/collection UI and end-to-end test flow. | Core MVP: billing → token → counter → ready → collection. |
| 9 | Review 2 | Present stable backend, data model and concurrency evidence. | Present integrated UI and live workflow demonstration. | Review 2: working prototype and progress against plan. |
| 10 | Slot booking | Implement slot/capacity model and safe capacity reservation. | Build slot picker, online pre-order and checkout screens. | Capacity-controlled pre-order flow with mock payment. |
| 11 | Real-time and reliability | Complete race-condition/idempotency tests; improve event logging. | Integrate WebSockets, reconnect behaviour and polling fallback. | Reliable updates and documented failure/recovery behaviour. |
| 12 | Analytics and optional forecast | Expose/export consistent event data and SQL reports. | Build charts and compare metrics; try demand forecasting only if data supports it. | Analytics dashboard and evidence-based results. |
| 13 | Evaluation | Run backend load/concurrency tests and support pilot/simulation. | Analyse before/after observations, usability and charts. | Evaluation results and limitations. |
| 14 | Report and presentation | Write architecture, database, backend, OS and testing sections. | Write UI, analytics, results and visual material sections. | Complete report draft and 20–30 slide presentation draft. |
| 15 | Final review and viva | Fix backend defects; prepare API, DB and OS explanations. | Fix UI defects; prepare workflow, networks and analytics explanations. | Rehearsed demo, final report, code and viva readiness. |

## 6. Build scope and technical hand-offs

### Build in this order

| Priority | Feature | Owner / hand-off |
|---|---|---|
| **MVP first** | Menu and walk-in order creation | Member 1 exposes endpoints; Member 2 builds menu/POS screens. |
| **MVP first** | Payment confirmation record and token generation | Member 1 implements rules; Member 2 shows confirmation/token. |
| **MVP first** | Counter-specific ticket dispatch and status updates | Member 1 creates tickets/status API; Member 2 builds counter dashboard. |
| **MVP first** | Token/QR verification and collection | Member 1 validates once-only redemption; Member 2 implements scan/type UI. |
| **Next** | Slot booking and capacity control | Member 1 owns transactional capacity; Member 2 builds slot selection and feedback. |
| **Next** | Online pre-order with mock payment | Member 1 owns payment/order state; Member 2 owns checkout screens. |
| **Next** | Live updates and analytics | Member 1 publishes events/WebSocket messages; Member 2 consumes updates and builds reports. |
| **Optional** | Demand forecasting | Member 2 explores forecasting; Member 1 connects approved capacity suggestions only if useful. |

### Technical hand-off rules

1. Member 1 must publish the endpoint, JSON fields, status codes and example response before Member 2 integrates a feature.
2. Member 2 should build against agreed API contracts. Use temporary mock data only while the real endpoint is being developed, and remove it from the final integrated flow.
3. Use one shared set of order/ticket statuses. Do not invent separate names in the backend and frontend.
4. PostgreSQL is the source of truth for orders, payments, capacity and collection. WebSocket messages notify clients; clients reload current state from REST after reconnecting.
5. Commit database migrations and API documentation with the code changes that depend on them.

### Recommended first-pass order statuses

- **Order:** `PENDING_PAYMENT` → `PAID` → `PARTIALLY_COLLECTED` → `COLLECTED` (with `CANCELLED`/`EXPIRED` outcomes where applicable).
- **Counter ticket:** `QUEUED` → `PREPARING` → `READY` → `COLLECTED` (with `UNCOLLECTED`/`CANCELLED` outcomes where appropriate).

Finalise the exact state transitions together before implementation.

### Scope control

| Must-have for a credible demo | Optional extensions / future work |
|---|---|
| Role-based screens; menu; walk-in order; payment confirmation record; unique token; counter tickets; status updates; collection verification; persistent database; basic logs and tests. | Real payment gateway; native mobile app; staff reassignment optimisation; advanced machine learning; inventory hardware integration; complex multi-branch support. |

> **Scope rule:** Finish the walk-in-to-token-to-counter-to-collection workflow before building pre-ordering. Slot booking is the next priority. Demand forecasting is optional and should only be attempted after enough usable data is available.

## 7. GitHub collaboration workflow

Keep one shared repository: [github.com/yo5on/DineDash](https://github.com/yo5on/DineDash). Both members use their own GitHub accounts and clone the same repository. Do not fork it if both are collaborators.

### Routine for each work session

1. Update local `main`: `git switch main`, then `git pull origin main`.
2. Switch to your own feature branch. Merge the latest `main` into that branch when needed.
3. Implement one focused task; run the relevant tests and inspect `git status`.
4. Commit with a meaningful message, for example: `feat: add counter ticket status endpoint`.
5. Push the feature branch and open a Pull Request targeting `main`.
6. Ask the other member to review. Merge only after checks pass; avoid direct pushes to `main`.

### Example commands

```powershell
git switch main
git pull origin main
git switch feature/your-branch
git merge main
# make changes, then:
git add .
git commit -m "feat: describe the change"
git push -u origin feature/your-branch
```

### Suggested branch names

| Member | Suggested branch names |
|---|---|
| **Member 1** | `feature/backend-setup` · `feature/order-api` · `feature/counter-dispatch` · `feature/slot-capacity` · `feature/concurrency-tests` |
| **Member 2** | `feature/frontend-setup` · `feature/student-ui` · `feature/counter-ui` · `feature/admin-dashboard` · `feature/analytics` |

## 8. Definition of done

A feature is complete when:

- The feature works in the integrated application, not only on one developer’s machine.
- Input validation, success states and common error cases are handled.
- Relevant tests pass; no secrets, `.env` files or local database files are committed.
- API/schema changes are documented and shared with the other member.
- The change is committed on a feature branch and merged through a reviewed Pull Request.
- Both members can explain the feature and its role in the complete system.

## 9. Risks and decisions to validate early

1. Confirm with the faculty guide that a two-member team is allowed; the ADS481 guide specifies three members.
2. Get permission from canteen management before observing staff or collecting identifiable/order data. Prefer anonymous timing observations.
3. Confirm the actual counter layout, whether one bill can contain items from multiple counters, accepted payment methods and whether a pilot is permitted.
4. If a live pilot or real records are unavailable, evaluate with a clearly labelled simulated dataset and a load/queue simulation. Do not present simulated results as real.
5. Use mock payment confirmation in the prototype unless the canteen formally authorises a real payment integration.

## 10. Immediate next steps

1. Confirm that a 2-person team is permitted.
2. Obtain permission for canteen observations.
3. Agree on the Week 1 scope and the actual canteen workflow before parallel development.
4. Replace “Member 1” and “Member 2” with the team members’ names and agree on the ownership split.
