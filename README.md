# 🏘️ Apartment Management System

An enterprise-grade, full-stack multi-tenant Apartment Management Platform designed to streamline operations, communications, payments, visitor management, maintenance tracking, and amenities bookings for housing societies and residential complexes.

---

## 🚀 Key Modules & Capabilities

- 🔐 **Authentication & RBAC**: JWT-based authentication with fine-grained Role-Based Access Control (`ADMIN`, `RESIDENT`, `SECURITY`, `STAFF`).
- 🏢 **Apartments & Units**: Block, floor, unit numbering, occupancy status, and square footage management.
- 👥 **Residents & Tenancy**: Owner vs. tenant profiles, emergency contacts, move-in/move-out timestamps.
- 🎫 **Visitor Management**: Digital check-ins, pre-authorized guest invitations with QR codes, delivery agent logging, and security desk scanning.
- 🛠️ **Complaints & Maintenance**: Ticket lifecycle tracking (`OPEN`, `IN_PROGRESS`, `RESOLVED`, `CLOSED`), categories, technician assignment, and SLA alerts.
- 💳 **Maintenance Dues & Payments**: Invoice generation, payment recording, transaction reconciliation, and automated digital receipts.
- 🚗 **Parking Management**: Slot allocation (covered/open), vehicle registration, license plate lookups, and visitor parking passes.
- 🏊 **Amenities Booking**: Clubhouse, swimming pool, tennis court, and banquet hall scheduling with collision detection and capacity limits.
- 📢 **Notices & Notifications**: Society circulars, emergency announcements, and in-app bell notification stream.
- 📊 **Executive Analytics**: Revenue graphs, occupancy ratios, visitor trends, and complaint resolution timelines.

---

## 🏛️ System Architecture

```
                    APARTMENT PLATFORM
                           │
             ┌─────────────┴─────────────┐
             ↓                           ↓
        FRONTEND                      BACKEND
      (React + Vite)             (Spring Boot 3 / Java 21)
             │                           │
       ┌─────┴─────┐             ┌───────┴────────┐
       ↓           ↓             ↓                ↓
     Pages     Components    Controllers       Security (JWT)
                               ↓
                            Services
                               ↓
                           Repositories
                               ↓
                             MySQL (8.0)
                               +
                             Redis (Optional Cache)
```

---

## 📂 Project Structure

```
apartment-management-system/
│
├── frontend/              ← React 18 + Vite SPA with modular components & role routing
├── backend/               ← Spring Boot 3 (Java 21) feature-oriented REST microservices
├── database/              ← Normalized SQL schemas (01-09) and seed data
├── docs/                  ← Architecture, ERD, API contracts, security & deployment specs
├── docker/                ← Multi-stage Dockerfiles and container configurations
├── .github/workflows/     ← CI/CD pipeline automation
├── docker-compose.yml     ← Full-stack orchestration (MySQL, Backend, Frontend)
└── README.md
```

---

## 🛠️ Tech Stack

- **Frontend**: React 18, Vite, React Router 6, Axios, Lucide Icons, Modern CSS3
- **Backend**: Java 21, Spring Boot 3.3+, Spring Security 6, Spring Data JPA, JJWT, Lombok, Springdoc OpenAPI (Swagger UI)
- **Database**: MySQL 8.0, Hibernate ORM
- **Cache/Session**: Redis 7.0
- **DevOps**: Docker, Docker Compose, GitHub Actions

---

## ⚡ Quick Start

### 1. Prerequisites
- Docker & Docker Compose **OR**
- Java JDK 21+ & Maven 3.9+
- Node.js 18+ (Node 20+ recommended)
- MySQL 8.0+

### 2. Run with Docker Compose (Recommended)
```bash
# Build and spin up all containers in the background
docker-compose up --build -d

# Verify all containers are healthy
docker-compose ps
```
- Frontend UI: `http://localhost:3000`
- Backend API: `http://localhost:8080/api`
- Swagger UI Documentation: `http://localhost:8080/swagger-ui.html`

### 3. Run Locally (Development Mode)

#### Database Setup
Create MySQL database and populate tables:
```bash
mysql -u root -p < docker/mysql/init.sql
```

#### Backend Setup
```bash
cd backend
mvn clean spring-boot:run -Dspring-boot.run.profiles=dev
```

#### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

---

## 👥 Default Demo Credentials

| Role | Email | Password | Landing Route |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@apartment.com` | `admin123` | `/admin/dashboard` |
| **Resident** | `resident@apartment.com` | `resident123` | `/resident/dashboard` |
| **Security** | `security@apartment.com` | `security123` | `/security/dashboard` |
| **Staff** | `staff@apartment.com` | `staff123` | `/admin/complaints` |

---

## 📜 License
This project is licensed under the MIT License.
