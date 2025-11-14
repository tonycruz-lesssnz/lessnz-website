# Lessnz Feature Map  
*A Structured Breakdown of Product Capabilities*

## 1. Overview
This document outlines the major product features in Lessnz, the users each feature serves, where in the codebase they live, and how they will evolve.

---

# 2. Core User Roles

### Teacher
- Plans and conducts lessons  
- Assigns material and practice  
- Reviews submissions  
- Tracks payments  
- Manages student roster  

### Student
- Receives weekly guidance  
- Completes assigned tasks  
- Tracks practice  
- Submits recordings  
- Views resources  

---

# 3. Feature Breakdown

## 3.1 Lesson Scheduling
### Purpose  
Enable teachers to create, view, update, and manage lesson times.

### Users  
Teacher (primary), Student (view-only)

### Current Implementation  
- Calendar UI using `react-big-calendar`  
- Lesson entity in database  
- Express CRUD routes  

### Future Evolution  
- Automated rescheduling  
- Conflict detection  
- Availability-based smart scheduling  

---

## 3.2 Assignments
### Purpose  
Enable teachers to assign weekly tasks, exercises, repertoire, drills, or media.

### Users  
Teacher & Student

### Current Implementation  
- Assignment page in React  
- Drizzle ORM table  
- Basic CRUD routes  

### Future Evolution  
- AI-generated assignment suggestions  
- Rubrics  
- Auto-leveling tasks based on progress  
- Assignment templates  

---

## 3.3 Practice Tracking
### Purpose  
Help students develop practice consistency and build accountability.

### Users  
Students (primary), Teachers (insight)

### Current Implementation  
- Practice logs stored in database  
- Teacher views aggregated logs  

### Future Evolution  
- Practice streak engine  
- Smart reminders  
- Daily check-ins  
- Practice analytics and heatmaps  
- Habit coaching (AI-driven)  

---

## 3.4 Resource Library
### Purpose  
A centralized hub for sheet music, audio, video, fingerings, PDFs, exercises, etc.

### Users  
Teachers (create), Students (view)

### Current Implementation  
- Upload via Uppy  
- Stored in S3 or similar  
- Table stores metadata  

### Future Evolution  
- Categorization + tags  
- Preview thumbnails  
- Versioning  
- Shared libraries across teachers (future marketplace)  

---

## 3.5 Media Upload & Review
### Purpose  
Enable students to upload practice videos/audio for critique.

### Users  
Students (upload), Teachers (review)

### Current Implementation  
- S3 file uploads  
- Associations with assignments  

### Future Evolution  
- Inline waveform review  
- Video markup  
- AI-based performance insights  
- “Send feedback snippet” inline tool  

---

## 3.6 Payment Tracking
### Purpose  
Provide teachers with financial organization and visibility.

### Users  
Teachers

### Current Implementation  
- PaymentRecord entity  
- Manual entry  

### Future Evolution  
- Auto-invoicing  
- Auto-reminders  
- Stripe integration  
- Payment reconciliation engine  

---

## 3.7 Student Portal
### Purpose  
Give students a dedicated space for their learning.

### Users  
Students

### Current Implementation  
- Dashboard page  
- Assignment list  
- Practice tracker  
- Resource access  

### Future Evolution  
- Gamification  
- Achievements  
- Personalized learning paths  
- Habit nudges  
- Progress analytics  

---

## 3.8 Teacher Dashboard
### Purpose  
Home base for studio management.

### Users  
Teachers

### Current Implementation  
- Upcoming lessons  
- Tasks  
- Assignments  

### Future Evolution  
- Studio analytics  
- Flagged students  
- Payment insights  
- AI-generated weekly summaries  

---

## 3.9 Messaging & Communication (Future)
### Purpose  
Allow teacher–student communication inside the platform.

### Future Evolution  
- Lesson chat thread  
- Voice messages  
- AI-assisted quick replies  
- Automatic lesson recaps  

---

## 3.10 Studio Automation (Long-Term)
This is the “holy grail” and strategic differentiator.

### Capabilities  
- Automated billing  
- Automated reminders  
- Automated scheduling  
- Automated progress insights  
- Lesson summary generator  
- Smart suggestions for assignments  
- Behavior-change nudges  

### Business Impact  
Transforms Lessnz from a tool → into a **studio operating system**.

---

# 4. Summary
Lessnz has a comprehensive feature set that supports lesson planning, practice consistency, engagement, and studio administration. Every feature is designed to reduce friction, increase clarity, and improve learning outcomes across the teacher–student relationship.

