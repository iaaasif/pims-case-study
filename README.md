# PIMS — Project Inventory Management System

> Enterprise inventory, procurement, project resource and financial management platform for construction and real-estate operations.

## ⚠️ Actual Runtime Architecture

The important correction is:

**The PIMS application is run through TWO repositories:**

### 1. PIMS Backend
https://github.com/iaaasif/pims-backend

Private NestJS + TypeScript backend/API.

Responsibilities:
- REST API
- Authentication and JWT security
- Role-based authorization
- User management
- Projects
- Materials
- Inventory
- Inventory transfers
- Purchase Requisitions
- Purchase Orders
- Vendors
- Budget variance
- Audit logs
- Neon PostgreSQL access
- Swagger/OpenAPI documentation

### 2. LANDORA PIMS
https://github.com/iaaasif/Landora-pims

Private LANDORA implementation/client application.

Responsibilities:
- React web application
- User interface and UX
- Dashboard and business modules
- Inventory screens
- Procurement screens
- Financial screens
- Reports and analytics
- API client integration
- Firebase-related notifications
- Capacitor Android application
- LANDORA-specific implementation

The repository iaaasif/pims is **not treated as the runtime/application repository in this case study**.

---

## 🏗️ System Architecture

```
                    PIMS USERS
               Web Browser / Android
                        │
                        ▼
             ┌─────────────────────┐
             │    LANDORA-PIMS     │
             │ React + Vite + TS   │
             │ Web + Capacitor     │
             └──────────┬──────────┘
                        │
                   HTTPS REST API
                        │
                        ▼
             ┌─────────────────────┐
             │    PIMS-BACKEND     │
             │ NestJS + TypeScript │
             │ Auth / RBAC / Logic │
             │ REST API            │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │  Neon PostgreSQL    │
             │      Database       │
             └─────────────────────┘
```

### Separation of Responsibilities

| Layer | Repository | Responsibility |
|---|---|---|
| Client/Application | Landora-pims | UI, web application, Android |
| Backend/API | pims-backend | Auth, RBAC, business logic, REST API |
| Database | Backend-managed | Neon PostgreSQL |
| Mobile | Landora-pims | Capacitor Android |
| API Documentation | pims-backend | Swagger/OpenAPI |
| Notifications | Application/backend integration | Firebase-related notifications |

---

# 🎯 Business Problem

Construction and real-estate businesses often manage materials, procurement, projects, vendors and expenses across multiple locations.

PIMS addresses problems such as:

- Manual stock tracking
- Spreadsheet-based inventory
- Poor project-site visibility
- Uncontrolled material transfers
- Manual purchase requisitions
- Slow approval workflows
- Scattered vendor information
- Difficult budget monitoring
- Weak audit trails
- Repetitive reporting

---

## 💡 PIMS Solution

PIMS connects the operational workflow:

```
Projects
   ↓
Locations
   ↓
Materials
   ↓
Inventory
   ↓
Procurement
   ↓
Vendors
   ↓
Financial Tracking
   ↓
Reports & Analytics
```

The backend provides authoritative business rules and data access, while LANDORA-PIMS provides the user-facing web and Android experience.

---

# 🚀 Core Modules

## Projects
- Construction project management
- Project-level information
- Budget information
- Project inventory visibility
- Budget variance analysis

## Materials
- Central material catalog
- Units
- Material classification
- Stock-related information

## Inventory
- Real-time stock ledger
- Stock transactions
- Material receipts
- Material issues
- Material consumption
- Low-stock alerts
- Project/location allocation

## Inventory Transfers
- Inter-project transfers
- Transfer requests
- Approval workflow
- Origin/destination tracking
- Transfer history

## Purchase Requisition

```
Requirement
    ↓
Purchase Requisition
    ↓
Review
    ↓
Approval / Rejection
```

## Purchase Order

```
Approved PR
    ↓
Purchase Order
    ↓
Vendor
    ↓
Procurement
    ↓
Material Receipt
```

## Vendor Management
- Supplier records
- Vendor search
- Vendor ratings/performance
- Procurement history

## Reports & Analytics
- Inventory
- Stock movements
- Material consumption
- Procurement
- Vendors
- Project costs
- Budget variance
- Inventory valuation
- Operational analytics

## Administration
- User management
- Roles
- Permissions
- Authentication
- System configuration
- Audit logs

---

# 🔐 Backend Security

The PIMS backend is built with NestJS and TypeScript and uses:

- Passport JWT authentication
- Role-based authorization
- Current-user guards
- Role guards
- Public-route controls
- DTO validation
- Class-validator
- Class-transformer
- Modular domain architecture
- Audit logging

The backend manages database access and server-side secrets.

---

# 🛠️ Technology Stack

## PIMS Backend

| Area | Technology |
|---|---|
| Framework | NestJS 10+ |
| Language | TypeScript |
| API | REST |
| Database | Neon PostgreSQL 16+ |
| Driver | pg |
| Authentication | Passport JWT |
| Authorization | Role-based guards |
| Validation | class-validator / class-transformer |
| Documentation | Swagger / OpenAPI |

## LANDORA PIMS

| Area | Technology |
|---|---|
| UI Framework | React 19 |
| Language | TypeScript |
| Build Tool | Vite |
| Styling | Tailwind CSS |
| UI | Radix UI |
| Routing | React Router |
| Charts | Recharts |
| Forms | React Hook Form |
| Validation | Zod |
| Icons | Lucide React |
| Notifications | Firebase / Sonner |
| Mobile | Capacitor 8 |
| Android | Native Android project |

---

# 📱 Web + Android

LANDORA-PIMS supports both web and Android application delivery.

### Web

```
React
  ↓
Vite Build
  ↓
Production Web Application
```

### Android

```
React Application
      ↓
Vite Build
      ↓
Capacitor
      ↓
Android Project
      ↓
APK / AAB
```

The application communicates with the backend API rather than exposing production database credentials to the client.

---

# 🔄 End-to-End Procurement Workflow

```
Project
   ↓
Material Requirement
   ↓
Purchase Requisition
   ↓
Approval
   ↓
Purchase Order
   ↓
Vendor
   ↓
Material Receipt
   ↓
Inventory Update
   ↓
Project Consumption
   ↓
Financial Tracking
   ↓
Reports
```

---

# 📊 Backend API

The backend documents APIs for:

- Health checks
- Authentication
- Users
- Projects
- Materials
- Inventory
- Inventory alerts
- Inventory transactions
- Inventory transfers
- Purchase requisitions
- Purchase orders
- Vendors
- Audit logs

Swagger/OpenAPI provides interactive API documentation.

---

# 📁 Repository Structure

```
PIMS Ecosystem
│
├── pims-backend/
│   ├── Auth
│   ├── Users
│   ├── Projects
│   ├── Materials
│   ├── Inventory
│   ├── Vendors
│   ├── Purchase Requisitions
│   ├── Purchase Orders
│   ├── Audit Logs
│   └── System
│
└── Landora-pims/
    ├── React Application
    ├── UI Components
    ├── Pages
    ├── API Client
    ├── Reports
    ├── Android
    └── Capacitor
```

---

# 🎨 Product Design Philosophy

**Design → Structure → Control → Automation → Reporting**

PIMS focuses on:

- Business-first workflows
- Clear operational dashboards
- Responsive UI
- Mobile accessibility
- Role-based access
- Centralized data
- Auditability
- Modular architecture

---

# 🔒 Privacy & Commercial Source Code

The runtime repositories are private.

This public case study intentionally does not expose:

- Database credentials
- JWT secrets
- API keys
- Environment secrets
- Production business data
- Private source code
- Customer information

---

# 👨‍💻 Developer

## Abdullah Al Asif

**Graphic Designer • Software Developer • CSE Engineer**

PIMS combines:

**UI/UX + Software Engineering + Construction Operations + Inventory + Procurement + Automation**

---

# 📌 Project Architecture Summary

The actual PIMS application is:

**LANDORA-PIMS Client + PIMS Backend + Neon PostgreSQL**

> **Current scope note:** Financial Tracking is not included in the current implemented PIMS scope documented here. Future financial/accounting modules should be added only when they are actually implemented in the runtime repositories.

with web and Android clients communicating through the backend REST API.

---

## 🔗 Runtime Repositories

- https://github.com/iaaasif/pims-backend
- https://github.com/iaaasif/Landora-pims

⭐ **Design it. Build it. Automate it. Improve it.**
