# 🌟 Platform Feature & Capability Directory
### *Functional Breakdown of the MOT-IGU Student Union SaaS Platform*

---

## 📋 1. Functional Modules Overview

| Module Name | Target Users | Primary Functional Benefit | Key Feature Highlight |
| :--- | :--- | :--- | :--- |
| **Academic Hub** | All Students | Interactive Q&A and drive file sharing. | Covers 60+ IGU departments with EN/TR filter. |
| **Housing Board** | Incoming & Current Students | Find verified flatmates and apartments near campus. | Strict 2-phase moderation pipeline. |
| **Used Tools Market**| All Students | Buy/Sell secondhand tools and textbooks in ₺. | Circular student economy & cost reduction. |
| **Campus Directory** | All Students | Quick access to official university offices. | Single-click email copy & direct phone dial. |
| **Survival Guide** | Freshmen & International | Residency (*İkamet*), transport card, and grading info. | Dynamic CMS articles updated by leadership. |
| **Admin CMS Suite** | Union Board & Admins | Complete governance over content and users. | User management, approval queues, full CRUD. |
| **Urgent Help Desk** | Students in Need | Direct help request triage by union teams. | Ticket resolution workflow (`pending`/`resolved`). |
| **Feedback Box** | All Students | Share sensitive suggestions anonymously. | Zero identity logging telemetry. |

---

## 🔍 2. Deep-Dive Feature Specifications

### 🎓 Module 1: Crowdsourced Academic Community Hub
- **Hierarchical Classification:** Level 1: Degree Level (*Lisans / Ön Lisans / Lisansüstü*) $\rightarrow$ Level 2: Faculty $\rightarrow$ Level 3: Department & Language $\rightarrow$ Level 4: Academic Year $\rightarrow$ Level 5: Open Classroom Feed.
- **Multilingual Search Engine:** Real-time query matching across Arabic, English, and Turkish names (e.g., searching for *"Computer"*, *"Yazılım"*, *"حاسوب"*, or *"Diş"*).
- **Interactive Open Classrooms:** Per-department, per-year open feeds where students post questions, share Google Drive lecture materials, and exchange solutions with batch peers.
- **Nested Discussions:** Allows students and senior batch mentors to reply directly to queries with attached solution files.

### 🏠 Module 2: Moderated Housing & Flatmate Board
- Designed specifically for students looking for accommodation around Avcılar and Istanbul campuses.
- **Anti-Spam State Machine:** Listings submitted by students enter a `pending` state, protecting students from unverified brokers or fraud.
- **Admin Moderation:** Union leadership can approve or reject listings with a single click.

### 🔄 Module 3: Used Study Supplies & Textbooks Marketplace
- Circular student economy for secondhand textbooks, T-squares, engineering calculators, and medical lab equipment.
- Features direct pricing in Turkish Liras (₺ / TL), condition status (*مستعمل بحالة جيدة*), and stock quantity tracking.

### 📞 Module 4: Administrative Directory & Telemetry
- Categorized directory for:
  - Student Affairs (*Öğrenci İşleri*)
  - International Students Office (*Uluslararası Ofis*)
  - Financial Affairs (*Mali İşler*)
  - Health, Culture, and Sports Directorate (*SKS*)
  - Faculty Deans' Offices
  - Campus Security & Facility Management
- **Single-Click Telemetry:** One-click copy-to-clipboard for emails and direct telephone dialing.

### 📖 Module 5: Residency & Campus Survival Guide
- Step-by-step guidance on:
  - Residence Permit (*İkamet*) application procedures and Göç İdaresi paperwork.
  - Discounted Istanbul Student Transport Card (*İstanbulkart*).
  - Academic portals guide (*OBIS / ALMS* exam and grading systems).

### 🛡️ Module 6: Enterprise-Grade Admin CMS Dashboard
- **User Governance:** View all registered students with full metadata (phone, gender, academic year, college), promote/demote roles (`student` $\leftrightarrow$ `admin`), and delete accounts.
- **Moderation Queues:** Separate visual review queues for student housing and used marketplace items.
- **Live CRUD Modules:** Manage university emergency contacts, residency (*İkamet*) guides, event calendars, FAQ databases, and job/internship boards without touching code.

---

## 💼 3. Business & Social Impact

| Impact Metric | Traditional Setup (Before) | MOT-IGU Platform (After) |
| :--- | :--- | :--- |
| **Communication** | Fragmented across dozens of WhatsApp groups | Centralized, searchable, open academic feeds |
| **Ad Verification** | Unchecked scams and unorganized messages | Verified, union-approved housing and supplies |
| **Onboarding** | Confusing residency and campus paperwork | Centralized, up-to-date bilingual survival guide |
| **Cost to Union** | High software development & hosting costs | **$0.00 / month** on optimized cloud serverless tier |
