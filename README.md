# PIMS — Project Inventory Management System

> Enterprise resource, multi-location inventory, procurement and financial tracking platform for construction and project-based operations.

**Product:** PIMS — Project Inventory Management System  
**Repository:** `iaaasif/pims`  
**Developer:** Abdullah Al Asif  
**Platforms:** Web + Android

---

## 📌 Project Overview

PIMS is a business-focused inventory and procurement management application designed for construction enterprises, engineering firms, project sites and distributed supply-chain operations.

The system brings project resources, inventory, procurement, vendors, financial tracking, approvals, reporting and notifications into a single application.

The case study in this repository is based **only on the original PIMS repository**:

urlPIMS — iaaasif/pimshttps://github.com/iaaasif/pims

No `pims-backend`, `Landora-pims`, or other repository is required to describe this case study.

---

## 🎯 Problem

Project-based businesses often manage materials and purchasing through spreadsheets, paper documents, messages and disconnected systems.

Typical problems include:

- Limited visibility of stock across locations
- Manual purchase requisition and approval processes
- Difficulty tracking material consumption
- Stock discrepancies between sites
- Slow procurement workflows
- Difficult vendor and purchase tracking
- Manual financial reconciliation
- Repetitive reporting work
- Limited real-time operational visibility

PIMS is designed to centralize these workflows.

---

## 💡 Solution

PIMS provides a unified application for managing:

```
Projects
   ↓
Locations
   ↓
Materials & Inventory
   ↓
Procurement
   ↓
Vendors
   ↓
Financial Tracking
   ↓
Reports & Analytics
```

The platform combines operational data with approval workflows, stock movement tracking, financial information and business reporting.

---

## 🚀 Key Features

### 📦 Multi-Location Inventory

- Project/location-based inventory
- Material stock tracking
- Minimum stock thresholds
- Material allocation
- Material consumption records
- Stock movement history
- Inter-location stock transfers
- Destination receipt verification
- Low-stock alerts

### 🧾 Procurement

- Purchase Requisition (PR)
- Multi-item requisitions
- Department review
- Approval workflows
- Purchase Order (PO) creation
- Vendor assignment
- Purchase order management
- Vendor performance tracking
- Print-ready procurement documents

### 💰 Financial Tracking

- Project budget monitoring
- Actual expenditure tracking
- Budget variance
- Bill verification
- Invoice matching
- Bank and cash book records
- Petty cash management
- Expense claims
- VAT and tax records
- Financial audit trails

### 📊 Reports & Analytics

The repository documents a reporting layer containing **16+ analytical report views**, including areas such as:

- Stock movement
- Inventory valuation
- Vendor spending
- Project cost analysis
- Material usage
- Financial analysis
- ROI and timeline information
- Custom report generation

Reports support export-oriented workflows such as Excel, CSV and PDF.

### 🔐 Access Control

The product is designed around role-based access control and approval hierarchies.

Documented roles include:

- Admin
- Management / Manager
- Storekeeper
- Accountant
- User

Permissions are intended to control access to operational and approval functions.

> Credentials and sensitive authentication information from development documentation are intentionally not reproduced in this public case study.

### 🔔 Notifications

Firebase is used for real-time notification and broadcast functionality.

The application is designed to surface operational events and alerts without requiring users to repeatedly refresh the application.

### 🌓 Adaptive UI

PIMS supports:

- Light and dark themes
- Responsive layouts
- Mobile-oriented navigation
- Android system bar handling
- Adaptive native/web presentation

---

## 🏗️ System Architecture

The original repository describes a client-focused cloud architecture:

```
                    ┌─────────────────────────┐
                    │       User / Client     │
                    │  Web Browser / Android  │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   React + TypeScript    │
                    │       PIMS Frontend     │
                    └───────┬─────────┬───────┘
                            │         │
                 ┌──────────┘         └──────────┐
                 ▼                               ▼
      ┌─────────────────────┐          ┌─────────────────────┐
      │ Neon / PostgreSQL   │          │      Firebase       │
      │ Data & persistence  │          │ Notifications/RT   │
      └─────────────────────┘          └─────────────────────┘
                            │
                            ▼
                  ┌─────────────────────┐
                  │  Business Modules   │
                  │ Inventory / PR / PO │
                  │ Finance / Reports   │
                  └─────────────────────┘
```

The repository also contains Supabase-related dependencies and product requirements for authentication/data workflows. The implementation has therefore evolved across multiple data/auth integration approaches; this case study intentionally describes the repository at a product/architecture level rather than claiming a separate backend repository.

---

## 🛠️ Technology Stack

| Area | Technology |
|---|---|
| Frontend | React 19 |
| Language | TypeScript 5.9 |
| Build Tool | Vite 7 |
| Styling | Tailwind CSS 3 |
| UI Primitives | Radix UI |
| Database | Neon Serverless PostgreSQL |
| Additional Data/Auth Integration | Supabase |
| Realtime Notifications | Firebase |
| Routing | React Router 7 |
| Charts | Recharts |
| Icons | Lucide React |
| Forms | React Hook Form |
| Validation | Zod |
| Mobile | Capacitor 8 |
| Android | Native Android project |
| Deployment Direction | Vercel / cPanel-compatible web deployment |

---

## 📂 Repository Structure

The original PIMS repository is organized around a single application codebase:

```
pims/
├── android/                  # Native Android / Capacitor project
├── src/
│   ├── components/           # Reusable UI & domain components
│   │   ├── admin/
│   │   ├── layout/
│   │   ├── procurement/
│   │   └── ui/
│   ├── context/              # Application contexts
│   ├── hooks/                # Reusable business/application hooks
│   ├── lib/                  # Database, Firebase & utility integrations
│   ├── pages/                # Application pages/modules
│   └── App.tsx               # Application entry
├── capacitor.config.ts       # Android/Capacitor configuration
├── vite.config.ts            # Vite build configuration
├── tailwind.config.js        # Tailwind configuration
├── package.json              # Dependencies & scripts
└── PRD.md                    # Product requirements
```

This structure keeps the core product in one maintainable application repository while separating UI components, business hooks, integrations and platform-specific Android code.

---

## 📱 Web + Android

One of the main strengths of the project is its dual-platform direction.

### Web

The React/Vite application can be built as a production web bundle.

Typical workflow:

```bash
npm install
npm run build
npm run preview
```

The repository also documents deployment of the generated `dist/` build to hosting environments such as cPanel.

### Android

PIMS uses Capacitor to package the web application into a native Android application.

Documented workflow:

```bash
npm run build
npx cap sync android
npx cap open android
```

The repository contains the Android project under:

```
android/
```

---

## 🧩 Core Business Modules

### 1. Dashboard
Operational overview and real-time business metrics.

### 2. Locations
Management of project/site/warehouse locations.

### 3. Projects
Project-level organization of resources and activities.

### 4. Materials
Material master data and inventory control.

### 5. Inventory
Stock quantities, movement, allocation and consumption.

### 6. Transfers
Movement of materials between locations.

### 7. Procurement
Purchase requisitions, approvals and purchase orders.

### 8. Vendors
Vendor information and procurement performance tracking.

### 9. Financial Management
Budgets, expenses, bills, cash and tax-related records.

### 10. Reports
Operational, inventory, procurement and financial analytics.

### 11. Administration
Users, permissions, settings and system-level controls.

### 12. Notifications
Real-time operational alerts and system broadcasts.

---

## 🔄 Example Procurement Workflow

```
Purchase Requisition
        ↓
Department Review
        ↓
Approval
        ↓
Purchase Order
        ↓
Vendor Assignment
        ↓
Purchase
        ↓
Material Receipt
        ↓
Inventory Update
        ↓
Financial / Bill Tracking
```

This workflow is designed to connect procurement activity with inventory and financial records instead of treating each process as an isolated task.

---

## 📦 Inventory Workflow

```
Material Receipt
       ↓
Location Stock
       ↓
Allocation / Issue
       ↓
Material Consumption
       ↓
Stock Movement
       ↓
Transfer / Reconciliation
       ↓
Reports & Valuation
```

This provides a traceable operational history for project materials.

---

## 📊 Reporting Architecture

PIMS treats reporting as a core part of the product rather than an afterthought.

The repository documents report categories covering:

- Inventory
- Stock movement
- Material usage
- Procurement
- Vendor spending
- Project cost
- Financial information
- Valuation
- ROI / timeline analysis

A custom report builder is also documented for selecting report columns and exporting data.

---

## 🎨 Product Design Philosophy

PIMS is designed around:

**Operational clarity → Structured data → Controlled workflows → Actionable reporting**

The UI emphasizes:

- Clear navigation
- Responsive layouts
- Reusable components
- Consistent forms
- Business-oriented dashboards
- Accessible UI primitives
- Mobile usability
- Light/dark theme support

---

## 🔒 Security & Privacy

PIMS is intended for business and operational data.

The public case study therefore does **not** expose:

- Production credentials
- Database passwords
- API secrets
- Private environment variables
- Real business credentials
- Sensitive customer information

The original repository's development documentation may contain example configuration material; sensitive values are intentionally excluded from this case study.

---

## 🧪 Development & Quality

The repository provides standard development scripts:

```bash
# Development
npm run dev

# Production build / TypeScript check
npm run build

# Linting
npm run lint

# Local production preview
npm run preview
```

The project also uses TypeScript, ESLint and production build verification as part of its development workflow.

---

## 🧠 Development Approach

PIMS is built around real business workflow requirements rather than being a generic inventory demo.

The development approach combines:

- Business process analysis
- UI/UX design
- React application development
- TypeScript
- Database integration
- Mobile packaging
- Real-time notifications
- Reporting and analytics
- AI-assisted development
- Iterative product development

---

## 📈 Product Goals

The PIMS product direction is focused on:

1. Centralizing project and inventory information
2. Reducing manual administrative work
3. Improving procurement visibility
4. Connecting inventory with financial tracking
5. Providing real-time operational information
6. Creating reliable audit trails
7. Supporting both office and field users
8. Building a scalable foundation for additional business modules

---

## 👨‍💻 Developer

### Abdullah Al Asif

**Graphic Designer • Software Developer • CSE Engineer**

PIMS reflects a combination of:

**Design + Software Development + Business Operations + Automation**

The product is built from practical business requirements and focuses on converting real operational workflows into usable digital systems.

---

## 📌 Project Status

PIMS is an actively evolving product.

The repository includes:

- Production-oriented web application structure
- Android/Capacitor project
- Inventory workflows
- Procurement workflows
- Financial tracking
- Reporting
- Notifications
- Role-based access concepts
- Product requirements documentation

Additional modules can be added as business requirements evolve.

---

## 🔗 Source Repository

urlView the original PIMS repository on GitHubhttps://github.com/iaaasif/pims

---

⭐ **Design it. Build it. Automate it. Improve it.**
