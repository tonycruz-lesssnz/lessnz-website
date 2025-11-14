# Lessnz Architecture  
*A Hybrid Present–Future Technical Blueprint*

## 1. Overview  
Lessnz is currently a **React + Vite SPA** connected to a **Node/Express API** with **PostgreSQL** as the data layer. The system is evolving toward a more scalable full-stack architecture (Next.js or hybrid serverless).

This document outlines both:
- **Today’s architecture**  
- **The recommended evolution path**  

---

## 2. Current Architecture (Present State)

### 2.1 Client (React + Vite)
The client application handles:

- Dashboard UIs  
- Routing via `wouter`  
- Data fetching via `@tanstack/react-query`  
- State hydration and caching  
- Form workflows  
- Media handling  
- Role-based rendering  

**Styling:** TailwindCSS + Radix UI primitives  
**Build tool:** Vite  

### 2.2 Server (Node + Express)
The Express API provides:

- Authentication endpoints  
- CRUD for all entities (lessons, assignments, students, etc.)  
- Resource management (links to S3 or local storage)  
- Calendar logic  
- Billing records  
- File upload handling  
- Practice log ingestion  

### 2.3 Database (PostgreSQL + Drizzle ORM)
Drizzle provides:

- Fully typed schemas  
- Migrations  
- Type-safe queries  
- Strong organization of entities  
- Reliability and portability  

### 2.4 Infrastructure
Currently optimized for local dev:

- Node server process  
- PostgreSQL instance  
- (Optional) S3 for media  
- (Optional) Playwright for testing  

---

## 3. Entity Model (Core Domain)

### 3.1 Teacher
- id  
- user reference  
- studio settings  
- schedule availability  
- payment preferences  

### 3.2 Student
- id  
- teacher_id  
- contact info  
- lesson history  
- resource access  

### 3.3 Lesson
- id  
- teacher_id  
- student_id  
- scheduled time  
- notes  
- materials  

### 3.4 Assignment
- id  
- lesson_id  
- student_id  
- description  
- due date  
- resources  

### 3.5 Practice Log
- id  
- student_id  
- date  
- duration  
- comments  
- media upload (optional)  

### 3.6 Payment Record
- id  
- teacher_id  
- student_id  
- amount  
- method  
- status  

### 3.7 Resource
- id  
- teacher_id  
- file  
- type  

---

## 4. Data Flows

### 4.1 Teacher Workflow
1. Creates lesson →  
2. Assigns materials →  
3. Student completes work →  
4. Teacher reviews →  
5. Progress updates generate insights  

### 4.2 Student Workflow
1. Receives expectations →  
2. Tracks practice →  
3. Uploads recordings →  
4. Receives teacher feedback →  
5. Progress loop continues  

### 4.3 Admin Workflow (Future)
1. System generates invoices →  
2. Sends reminders →  
3. Tracks payments →  
4. Identifies trends →  
5. Automates scheduling  

---

## 5. Recommended Future Architecture (12–18 Months)  
Lessnz should evolve toward:

### Option A — **Next.js Full-Stack Architecture**
Benefits:
- Unified client/server  
- File-system routing  
- API routes built-in  
- Server components reduce payload  
- Edge functions for automation  
- Superior SEO for landing site  
- Simpler deployments (Vercel)  

### Option B — **Hybrid Serverless**
- Express becomes minimal  
- Serverless functions handle API  
- Postgres via Supabase or Neon  
- Media on S3 or R2  
- Auth via Clerk or Supabase Auth  

### Option C — **Studio Automation Engine**
Domain logic extracted into services:

- BillingService  
- SchedulingService  
- PracticeAnalyticsService  
- NotificationService  
- LessonSummarizer (AI)  

---

## 6. Security Model  
The system enforces role-based access:

- `teacher` can create and manage lesson data  
- `student` can only access assigned material  
- `admin` (future) will support studio-level operations  

All endpoints require:

- Auth token  
- Role validation  
- Entity-level ownership checks  
- Sanitized input  

---

## 7. Summary  
Lessnz’s architecture is clean, modern, and extensible. With a thoughtful evolution path, it can transform from a traditional SPA + backend API into a scalable, serverless or Next.js-driven platform capable of supporting multi-teacher studios and fully automated administrative workflows.

