# Lessnz Data Flow Diagrams  
*Structured, Academic, and Clear Visual Models of the System*

This document contains Mermaid-based diagrams and structured textual descriptions of how data moves through Lessnz across the core teaching and learning workflows.

---

# 1. Teacher–Student Weekly Cycle (High-Level)

The weekly loop between teacher and student is the beating heart of Lessnz.

```mermaid
flowchart LR
    Teacher[Teacher Creates Lesson & Assignments] --> DB[(Database)]
    DB --> Student[Student Receives Expectations]
    Student --> Practice[Practice Logging + Media Upload]
    Practice --> DB
    DB --> Review[Teacher Reviews Work]
    Review --> Feedback[Feedback to Student]
    Feedback --> DB
    DB --> Insights[Progress Insights (Future)]
	
Lesson Creation Workflow
sequenceDiagram
    participant T as Teacher
    participant C as Client (React)
    participant API as Express API
    participant DB as PostgreSQL

    T->>C: Create new lesson (UI form)
    C->>API: POST /lessons
    API->>DB: Insert lesson record
    DB-->>API: Lesson created
    API-->>C: Return JSON
    C-->>T: Updated schedule view
	
Assignment Workflow
sequenceDiagram
    participant T as Teacher
    participant C as Client
    participant API as Express API
    participant DB as PostgreSQL
    participant S as Student

    T->>C: Create assignment
    C->>API: POST /assignments
    API->>DB: Insert assignment
    DB-->>API: Success
    API-->>C: Assignment saved
    C-->>S: Assignment appears in student portal (React Query)
	
Practice Logging Workflow
flowchart LR
    S[Student] --> UI[Practice Log Form]
    UI --> API[POST /practice]
    API --> DB[(practice_logs)]
    DB --> TeacherView[Aggregated Teacher Dashboard]

Media Upload Workflow
sequenceDiagram
    participant S as Student
    participant C as Client
    participant U as Upload Handler (Uppy/S3)
    participant API as Express API
    participant DB as PostgreSQL

    S->>C: Select file to upload
    C->>U: Direct upload to S3 (signed URL)
    U-->>C: Upload success
    C->>API: POST /media (metadata)
    API->>DB: Insert media record
    DB-->>API: Success
    API-->>C: Media attached

Payment Tracking Workflow
flowchart LR
    Teacher --> UI[Enter Payment or Trigger Invoice (future)]
    UI --> API[POST /payments]
    API --> DB[(payment_records)]
    DB --> TeacherView[Financial Overview]
	
Authentication Workflow
sequenceDiagram
    participant User
    participant Client
    participant API
    participant DB

    User->>Client: Enter credentials
    Client->>API: POST /auth/login
    API->>DB: Validate user
    DB-->>API: Valid
    API-->>Client: JWT token
    Client-->>User: Authenticated session
	
Future: Automated Studio Admin Engine
flowchart LR
    DB[(Historical Data)] --> ML[Analytics & AI Service]
    ML --> Scheduler[Smart Scheduler]
    ML --> Billing[Auto-Invoice Engine]
    ML --> NudgeEngine[Practice Nudges]
    Scheduler --> API
    Billing --> API
    NudgeEngine --> API
    API --> UI






	
	
	
