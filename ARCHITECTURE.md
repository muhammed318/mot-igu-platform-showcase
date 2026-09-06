# 🏛️ System Architecture & Engineering Specifications
### *Deep Dive into Data Modeling, Cloud Topology, and API Design*

---

## ☁️ 1. Cloud Topology & Infrastructure Matrix

| Cloud Provider | Component | Purpose | Key Metric |
| :--- | :--- | :--- | :--- |
| **Vercel** | Frontend Edge CDN | Hosts React 18 SPA, handles global caching and SSL encryption. | Sub-100ms Global TTFB |
| **Render.com** | Backend Web Service | Containerized Node.js/Express.js RESTful API engine. | 99.9% Uptime, Zero Idle Billing |
| **Neon.tech** | PostgreSQL Database | Serverless relational database with auto-scaling compute. | Auto-suspend connection pooling |
| **GitHub** | Version Control & CI/CD | Automated deployment triggers on `main` branch push. | GitOps Deployment Pipeline |

---

## 🔐 2. Security & Authentication Architecture

| Layer | Implementation | Security Benefit |
| :--- | :--- | :--- |
| **Password Storage** | 10-Round Salted Bcrypt Hash | Protection against Rainbow Table and brute-force attacks. |
| **Session State** | Stateless JWT (JSON Web Tokens) | 7-day cryptographically signed bearer tokens; zero server RAM session overhead. |
| **Access Control (RBAC)** | `authMiddleware` & `adminMiddleware` | Dual-layer verification ensuring student vs. administrative route isolation. |
| **Environment Isolation** | Runtime Variables (`.env`) | Zero credentials or database URLs leaked into client-side code bundles. |
| **Fault Resilience** | `Promise.allSettled` Pattern | Guaranteed dashboard availability even when specific datasets are empty. |

---

## 📊 3. Relational Database Schema Matrix (PostgreSQL / Prisma)

The relational database consists of **14 interconnected models** optimized for query performance:

| Entity Name | Primary Key | Key Fields & Relations | Architectural Domain |
| :--- | :--- | :--- | :--- |
| **`User`** | `UUID (v4)` | `name`, `email` (unique), `password`, `phone`, `academicYear`, `gender`, `college`, `role` | Identity & RBAC |
| **`AcademicPost`** | `UUID (v4)` | `faculty`, `department`, `academicYear`, `title`, `content`, `type`, `fileUrl`, `authorName` | Crowdsourced Q&A |
| **`AcademicAnswer`** | `UUID (v4)` | `postId` (FK $\rightarrow$ `AcademicPost`), `content`, `fileUrl`, `authorName` | Community Discussion |
| **`College`** | `UUID (v4)` | `name`, `description`, `subjects` (1:N relation) | Academic Structure |
| **`Subject`** | `UUID (v4)` | `name`, `code`, `academicYear`, `collegeId` (FK), `gradingBreakdown` | Course Repository |
| **`Housing`** | `UUID (v4)` | `area`, `description`, `contactInfo`, `status` (`pending`/`approved`/`rejected`) | Moderated Board |
| **`Product`** | `UUID (v4)` | `name`, `price`, `stock`, `imageUrl`, `type`, `status` (`pending`/`approved`) | Student Marketplace |
| **`UniversityContact`** | `UUID (v4)` | `title`, `department`, `email`, `phone`, `location`, `workingHours` | Administrative Directory |
| **`GuideItem`** | `UUID (v4)` | `title`, `content`, `category` (`إقامة` / `مواصلات` / `دراسة` / `معيشة`) | Campus Knowledge Base |
| **`Event`** | `UUID (v4)` | `title`, `description`, `date`, `location`, `category` | Student Activities |
| **`HelpRequest`** | `UUID (v4)` | `name`, `email`, `requestType`, `details`, `status` (`pending`/`resolved`) | Support Triage |
| **`FAQ`** | `UUID (v4)` | `question`, `answer`, `category` | Automated Self-Help |
| **`Sponsor`** | `UUID (v4)` | `companyName`, `discountDetails`, `category`, `logoUrl` | Commercial Partnerships |
| **`BudgetReport`** | `UUID (v4)` | `title`, `description`, `amount`, `category`, `date` | Financial Transparency |

---

## 🌐 4. Core RESTful API Matrix

All API endpoints follow standardized JSON contracts:
- **Success:** `{ success: true, data: ... }`
- **Error:** `{ success: false, message: "..." }`

| Method | Route Endpoint | Access Level | Description |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Public | Register new student with verified academic year & phone. |
| `POST` | `/api/auth/login` | Public | Verify credentials and return signed JWT token. |
| `GET` | `/api/auth/me` | Authenticated | Retrieve authenticated user profile payload. |
| `GET` | `/api/auth/users` | Admin Only | List all registered university students. |
| `PATCH`| `/api/auth/users/:id/role` | Admin Only | Promote or demote user role (`student` $\leftrightarrow$ `admin`). |
| `DELETE`| `/api/auth/users/:id` | Admin Only | Permanently delete user record. |
| `GET` | `/api/academic-posts` | Public | Filter posts by `department` and `academicYear`. |
| `POST` | `/api/academic-posts` | Authenticated | Publish new question, summary, or lecture Drive link. |
| `POST` | `/api/academic-posts/:id/answers`| Authenticated | Submit community answer or attached solution file. |
| `DELETE`| `/api/academic-posts/:id` | Admin / Author | Remove discussion thread. |
| `GET` | `/api/housing` | Public | Retrieve approved student housing listings. |
| `GET` | `/api/housing/admin/all` | Admin Only | View full housing queue including pending submissions. |
| `POST` | `/api/housing` | Authenticated | Submit housing ad (Enters `pending` review state). |
| `PATCH`| `/api/housing/:id/status` | Admin Only | Moderate housing listing (`approved` / `rejected`). |
| `GET` | `/api/products` | Public | Retrieve verified used study tools and textbooks. |
| `POST` | `/api/products` | Authenticated | Submit used tool listing for review. |
| `PATCH`| `/api/products/:id/status` | Admin Only | Moderate used marketplace item. |
| `GET` | `/api/contacts` | Public | Search university directory by department and query. |
| `POST` | `/api/contacts` | Admin Only | Add official university contact information. |
| `DELETE`| `/api/contacts/:id` | Admin Only | Delete directory contact. |
| `GET` | `/api/guide` | Public | Retrieve survival and residency guidelines. |
| `POST` | `/api/guide` | Admin Only | Create dynamic guide article. |

---

## 🔄 5. State Machine: Content Moderation Pipeline
[ Student Form Submission ]
│
▼
{ status: "pending" } ───► Hidden from Public Feeds
│
[ Admin Review ]
│ │
▼ ▼
[ "approved" ] [ "rejected" ]
│ │
▼ ▼
Visible to All Removed / Archived
