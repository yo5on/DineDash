# DineDash – Two-Member Project Work Plan

**Project Title:** Demand-Aware Canteen Ordering and Real-Time Token Dispatch System

**Duration:** 15 Weeks  
**Team Size:** 2 Members  
**Repository:** https://github.com/yo5on/DineDash

---

## 1. Project Objective

DineDash aims to reduce congestion in the college canteen by digitising the ordering, billing and food distribution workflow.

Students can place orders through a mobile-friendly web application or the existing billing counter. Paid orders receive digital tokens and are automatically dispatched to their respective food counters.

Staff update preparation status, and students collect their food when ready.

The system will also provide analytics to monitor waiting times, peak-hour demand, counter utilisation and food popularity.

---

## 2. Division of Responsibilities

### Member 1 – Backend, Database and Operating Systems

**Primary Responsibility:** Backend development and system logic.

**Technologies:**
- Java 21
- Spring Boot
- PostgreSQL
- REST APIs
- Java Concurrency

**Responsibilities:**

1. Create and configure the Spring Boot backend.
2. Design the database schema and relationships.
3. Implement user authentication and role management.
4. Develop menu and food management APIs.
5. Implement order creation and management.
6. Implement payment confirmation logic.
7. Generate unique digital tokens and QR codes.
8. Implement automatic order dispatch to food counters.
9. Manage order status transitions.
10. Implement pickup verification.
11. Implement pickup slot and capacity management.
12. Handle concurrent bookings and race conditions.
13. Implement multithreading and synchronisation.
14. Write backend unit and integration tests.
15. Implement event logging and database transactions.

**Expected Deliverables:**

- Working Spring Boot backend.
- PostgreSQL database.
- REST API endpoints.
- Order and token management.
- Counter dispatch mechanism.
- Concurrency implementation and tests.
- Backend documentation.

### Member 2 – Frontend, Integration and Analytics

**Primary Responsibility:** User interfaces and data visualisation.

**Technologies:**

- React
- Vite
- JavaScript / TypeScript
- Python
- Pandas
- Matplotlib
- Chart.js

**Responsibilities:**

1. Set up the React frontend.
2. Design the application layout and navigation.
3. Develop the student dashboard.
4. Develop the food menu and ordering interface.
5. Implement shopping cart and checkout screens.
6. Develop the billing/POS interface.
7. Develop the food counter dashboard.
8. Develop the admin dashboard.
9. Integrate frontend screens with backend REST APIs.
10. Implement real-time order status updates.
11. Implement token display and QR scanning interface.
12. Build the analytics dashboard.
13. Analyse order and waiting-time data.
14. Create charts for peak hours, food popularity and counter utilisation.
15. Explore demand forecasting using machine learning if sufficient data is available.
16. Write frontend and integration tests.

**Expected Deliverables:**

- Working React application.
- Student ordering interface.
- Billing interface.
- Food counter dashboard.
- Admin dashboard.
- Analytics and visualisations.
- Frontend documentation.

---

## 3. Shared Responsibilities

Both members must work together on:

- Problem identification and finalisation.
- Literature survey and research.
- Requirement analysis.
- System architecture design.
- ER diagram and class diagram review.
- API contract planning.
- Integration testing.
- Performance evaluation.
- Project report.
- Presentation preparation.
- Final demonstration and viva.

Neither member should work in complete isolation. Both must understand the complete system.

---

## 4. Fifteen-Week Development Roadmap

| Week | Work to Complete | Member 1 | Member 2 |
|------|-----------------|-----------|-----------|
| 1 | Project finalisation | Backend requirements | Workflow research |
| 2 | Data collection and research | Database planning | Queue observations and literature survey |
| 3 | System design | ER and class diagrams | UI wireframes and architecture review |
| 4 | Development setup | Spring Boot setup | React setup |
| 5 | Review 1 preparation | Database and backend prototype | UI prototype and documentation |
| 6 | Core ordering | Order APIs and payment records | Menu and billing interface |
| 7 | Token dispatch | Token generation and counter tickets | Counter dashboard |
| 8 | Core MVP integration | Token verification and order status | Student tracking and collection UI |
| 9 | Review 2 | Backend demonstration | Complete UI demonstration |
| 10 | Pre-ordering | Slot and capacity management | Slot selection and checkout |
| 11 | Concurrency and real-time updates | Race-condition testing | WebSocket integration |
| 12 | Analytics | Event data and SQL reporting | Analytics dashboard and optional ML |
| 13 | Testing | Load and backend testing | UI testing and data analysis |
| 14 | Documentation | Backend, database and OS report | Frontend, analytics and results report |
| 15 | Final submission | Backend fixes and viva preparation | UI fixes and presentation preparation |

---

## 5. Project Development Phases

### Phase 1 – Foundation (Weeks 1–5)

**Tasks:**

- Finalise problem statement.
- Obtain faculty approval.
- Study the existing canteen workflow.
- Collect baseline waiting-time observations.
- Complete literature survey.
- Design architecture and database.
- Set up frontend and backend environments.

**Milestone:** Review 1 – Problem statement, objectives, architecture and diagrams.

### Phase 2 – Core System (Weeks 6–9)

**Tasks:**

- Student menu.
- Walk-in billing.
- Order creation.
- Payment confirmation.
- Digital token generation.
- Automatic counter dispatch.
- Counter staff dashboard.
- Order preparation status.
- Token verification and food collection.

**Milestone:** Working MVP and Review 2 demonstration.

### Phase 3 – Advanced Features (Weeks 10–12)

**Tasks:**

- Online pre-ordering.
- Pickup slot management.
- Capacity control.
- Concurrent booking prevention.
- Real-time notifications.
- Analytics dashboard.
- Optional demand forecasting.

**Milestone:** Complete integrated system.

### Phase 4 – Testing and Submission (Weeks 13–15)

**Tasks:**

- Integration testing.
- Performance testing.
- Concurrency testing.
- Waiting-time evaluation.
- Final report.
- Presentation.
- Demo and viva preparation.

**Milestone:** Final submission.

---

## 6. GitHub Collaboration Workflow

**Repository:** https://github.com/yo5on/DineDash

Both members will use the same repository with separate GitHub accounts.

### Member 1 Branches

- `feature/backend-setup`
- `feature/order-api`
- `feature/counter-dispatch`
- `feature/slot-capacity`
- `feature/concurrency-tests`

### Member 2 Branches

- `feature/frontend-setup`
- `feature/student-ui`
- `feature/counter-ui`
- `feature/admin-dashboard`
- `feature/analytics`

### Development Workflow

1. Pull the latest `main` branch.
2. Switch to your own feature branch.
3. Implement your assigned feature.
4. Test your changes.
5. Commit and push to GitHub.
6. Create a Pull Request.
7. Ask the other member to review.
8. Merge into `main` after approval.

**Important:** Never directly push unfinished work to `main`.

---

## 7. Feature Priority

### Must-Have Features

- Menu management.
- Walk-in billing interface.
- Order management.
- Digital token generation.
- Automatic counter dispatch.
- Counter staff dashboard.
- Order status tracking.
- Token verification.
- Database integration.
- Basic analytics.

### Should-Have Features

- Online pre-ordering.
- Pickup slot booking.
- Capacity management.
- Real-time notifications.
- Advanced analytics.

### Optional Extensions

- Food demand forecasting.
- QR-based collection.
- No-show analytics.
- Advanced queue optimisation.

### Out of Scope Initially

- Real payment gateway integration.
- Native Android application.
- Dynamic staff reassignment.
- Complex machine learning models.
- Microservices architecture.

---

## 8. Integration Rules

1. Member 1 must communicate API endpoints and response formats before Member 2 integrates them.
2. Both members must agree on order and ticket status names.
3. PostgreSQL must remain the source of truth for orders and payments.
4. WebSockets will deliver notifications, while REST APIs will retrieve the actual system state.
5. Database changes must be committed as migrations.
6. Both members must test their modules together regularly.

---

## 9. Definition of Completion

The project will be considered ready when:

- Students can place orders.
- Billing staff can process walk-in orders.
- Paid orders generate unique tokens.
- Orders reach the correct food counters.
- Staff can update preparation status.
- Students can verify and collect their orders.
- Concurrent bookings are handled safely.
- Analytics display meaningful operational metrics.
- The entire workflow can be demonstrated successfully.
- Documentation, tests, GitHub repository and presentation are complete.

---

## 10. Immediate Next Steps

1. Confirm the two-member arrangement with the faculty guide.
2. Obtain permission to observe the canteen workflow.
3. Complete GitHub repository setup for both members.
4. Finalise the system requirements.
5. Create the architecture diagram, ER diagram and class diagram.
6. Initialise React, Spring Boot and PostgreSQL.
7. Begin development with the walk-in ordering and digital token workflow.

---

## 11. Academic Note

The ADS481 Student Guide specifies three members per team. The proposed two-member arrangement must be approved by the faculty guide before finalising the team structure.

The 15-week schedule is based on the approximate timeline provided in the department's student guide.

---

**Project:** DineDash  
**Repository:** https://github.com/yo5on/DineDash  
**Duration:** 15 Weeks  
**Work Division:** Backend and Systems / Frontend and Analytics
