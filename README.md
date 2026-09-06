# 🇪🇬 🇹🇷 Egyptian Students' Union SaaS Platform (MOT - IGU)
### *A Production-Grade, Full-Stack Community & Academic Management Portal*

[![Live Demo](https://img.shields.io/badge/Live_Demo-Online-emerald?style=for-the-badge&logo=vercel)](https://egyptian-student-union.vercel.app)
[![Tech Stack](https://img.shields.io/badge/Stack-React_|_Node.js_|_PostgreSQL-blue?style=for-the-badge)](https://egyptian-student-union.vercel.app)
[![Database](https://img.shields.io/badge/Database-Neon_Serverless-cyan?style=for-the-badge&logo=postgresql)](https://neon.tech)
[![Cost](https://img.shields.io/badge/Infrastructure_Cost-$0.00_Free_Tier-green?style=for-the-badge)](#)

> 🔒 **Showcase Notice:** This repository serves as a **Public Architecture & Case Study Showcase**. The underlying proprietary source code is securely maintained in a private repository for intellectual property protection.

---

## 🌐 Live Application
- **Production URL:** [https://egyptian-student-union.vercel.app](https://egyptian-student-union.vercel.app)
- **Target Organization:** Egyptian Students' Union at Istanbul Gelişim University (*Mısırlı Öğrenciler Topluluğu - MOT IGU*).
- **Target Audience:** International Egyptian students across all university faculties and institutes in Istanbul, Turkey.

---

## 🚀 Project Overview
The **MOT-IGU Platform** is a scalable, full-stack web portal engineered to digitize student union operations and provide centralized academic and community services. 

Key problem solved: eliminating fragmented WhatsApp/Telegram groups by offering an **open, crowdsourced academic knowledge hub covering 60+ departments**, a **moderated student housing & marketplace board**, an **administrative contacts directory**, and a **role-based Content Management System (CMS)**.

---

## 🛠️ Complete Tech Stack & Architecture

```mermaid
graph TD
    A[🌐 Vercel Global Edge CDN<br/><b>React 18 • Vite • Tailwind CSS</b>] -->|HTTPS / RESTful API| B[⚙️ Render Cloud Web Service<br/><b>Node.js • Express.js • JWT • Bcrypt</b>]
    B -->|Connection Pooling / Prisma ORM| C[(🗄️ Neon Serverless PostgreSQL<br/><b>Relational DB • Auto-Scale</b>)]
Frontend (Client Layer)
React.js 18 (Vite): Lightweight Single Page Application (SPA) architecture.
Tailwind CSS v3: Custom design system with native Right-to-Left (RTL) support, responsive grid layouts, and brand palette synchronization.
React Router DOM v6: Declarative multi-page routing with protected admin route guards.
Lucide React: Modern vector icon library.
Context API: Stateless client session synchronization with JWT token management.
Backend (Server & Logic Layer)
Node.js & Express.js: Modular RESTful API architecture with structured error handling middleware.
JSON Web Tokens (JWT): Stateless bearer token authentication.
Bcrypt.js: Multi-round cryptographic password hashing.
Prisma ORM: Type-safe database client and automated relational schema migrations.
CORS Configuration: Strict cross-origin resource sharing policy for secure client-server communication.
Cloud Infrastructure & DevOps (0.00$ Cost)
Database: Serverless PostgreSQL on Neon.tech with auto-suspension to preserve compute units.
Backend Service: Containerized Node.js Web Service on Render.com.
Frontend Hosting: Global Edge CDN deployment on Vercel with instant CI/CD Git triggers.
🌟 Key Architecture & Functional Highlights
1. 🎓 Hierarchical Crowdsourced Academic Hub
60+ Programs Mapped: Full structure covering Bachelor's (Lisans), Vocational Schools (Ön Lisans - SHMYO & İGMYO), and Graduate Institutes (Lisansüstü).
Multilingual Search & Filtering: Instant filter by study language (🇬🇧 English, 🇹🇷 Turkish, or bilingual) and search across Arabic, English, and Turkish queries.
Interactive Open Classrooms: Per-department, per-year open feeds where students post questions, share Google Drive lecture materials, and exchange solutions with batch peers.
2. 🛡️ Two-Phase Ad Moderation Pipeline
Applied to Student Housing and Used Study Supplies (Marketplace).
Student submissions are quarantined in pending status until verified and approved (approved) by union admins via the dashboard to prevent spam and fraud.
3. ⚙️ Full Content Management System (Admin Dashboard)
Unified command center accessible strictly to users with the admin role.
User Governance: View all registered students with full metadata (phone, gender, academic year, college), promote/demote roles (student 
↔
↔
 admin), and delete accounts.
Live CRUD Modules: Manage university emergency contacts, residency (İkamet) guides, event calendars, FAQ databases, and job/internship boards without touching code.
4. 📞 University Administrative Directory
Searchable directory of official university departments (Öğrenci İşleri, Uluslararası Ofis, Mali İşler, SKS).
Features single-click copy-to-clipboard for emails and direct-dial integration for phone numbers.
5. 🔒 Anonymous Feedback Telemetry
Privacy-first submission channel with zero identity logging, empowering students to voice sensitive feedback safely.
📊 Relational Database Design (Prisma Schema)
The database schema includes 14 relational models:
Model	Purpose	Key Attributes
User	Authentication & User Metadata	id, name, email, phone, academicYear, gender, college, role
AcademicPost	Questions & Shared Resources	id, faculty, department, academicYear, title, content, type, fileUrl
AcademicAnswer	Community Thread Replies	id, postId, authorName, content, fileUrl, createdAt
Housing	Student Accommodation Listings	id, area, description, contactInfo, status (pending/approved)
Product	Secondhand Study Supplies Market	id, name, price, stock, imageUrl, status (pending/approved)
UniversityContact	University Offices Directory	id, title, department, email, phone, location, workingHours
GuideItem	Campus & Residency Survival Guide	id, title, content, category (إقامة / مواصلات / دراسة)
Event, FAQ, Job, Sponsor	Union Services Management	Mapped domain-specific attributes with full Admin CRUD
🔐 Security & Reliability Best Practices
Defense-in-Depth Authentication: Passwords hashed with 10-round Salted Bcrypt; API requests guarded by JWT verification middleware.
Fault-Tolerant Async Loading: The frontend dashboard utilizes Promise.allSettled to guarantee seamless UI rendering even if specific datasets are empty.
Environment Isolation: Zero credentials leaked; all connection strings, secrets, and origins are injected via runtime environment variables.
👨‍💻 Author & Developer
Muhammed Eid — Full-Stack Software Engineer
GitHub: @muhammed318
Live Production Application: https://egyptian-student-union.vercel.app
