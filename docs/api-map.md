
---

# --------------------------------  
# 📘 `docs/api-map.md`  
# --------------------------------

```markdown
# Lessnz API Map  
*Comprehensive Documentation of Backend Endpoints*

This API map is designed for clarity, onboarding speed, and long-term maintainability. It covers authentication, users, lessons, assignments, practice logs, resources, media, payments, and future endpoints.

---

# 1. Authentication

## POST /auth/register
Create a new user account.  
**Roles:** teacher, student  
**Body:** email, password, role  

## POST /auth/login
Authenticate user.  
**Returns:** JWT token + user metadata  

---

# 2. Users

## GET /users/me
Retrieve the current authenticated user.  
**Auth:** required  

## GET /users/:id
Retrieve user profile data.  
**Auth:** role-specific access  

---

# 3. Teachers

## GET /teachers/:id
Fetch teacher profile, settings, roster.  

## PATCH /teachers/:id
Update teacher settings (studio info, availability).  

---

# 4. Students

## GET /students
List students for a teacher.  

## POST /students
Add new student.  

## GET /students/:id
Get student details.  

## PATCH /students/:id
Update student info.  

---

# 5. Lessons

## GET /lessons
Get lessons for teacher or student (filtered by role).  

## POST /lessons
Create a new lesson.  
**Body:** teacher_id, student_id, datetime, notes  

## PATCH /lessons/:id
Update lesson.  

## DELETE /lessons/:id
Remove lesson.  

---

# 6. Assignments

## GET /assignments?student_id=
List assignments for a student.  

## POST /assignments
Create assignment.  

## PATCH /assignments/:id
Update assignment.  

## DELETE /assignments/:id
Delete assignment.  

---

# 7. Practice Logs

## GET /practice?student_id=
List practice logs.  

## POST /practice
Submit practice session.  
**Body:** duration, notes, media_id  

---

# 8. Resources

## GET /resources
List resources (PDF, audio, video).  

## POST /resources
Upload new resource (metadata).  
Uploads are performed via a signed URL workflow (Uppy → S3).  

---

# 9. Media

## POST /media/signed-url
Generate signed URL for direct uploads.  

## POST /media
Store metadata for uploaded file.  

## GET /media/:id
Retrieve media metadata.  

---

# 10. Payments

## GET /payments
List payment records.  

## POST /payments
Create payment entry.  

## PATCH /payments/:id
Update payment status.  

---

# 11. Notifications (Future)

## POST /notifications/send
Send email/SMS/push notifications.  

## POST /notifications/schedule
Schedule automated reminders.  

---

# 12. Automation Engine (Future)

## POST /automation/invoices/generate
Auto-generate invoices.  

## POST /automation/lessons/summarize
Generate AI-based lesson summaries.  

## POST /automation/nudges/send
Send practice nudges.  

---

# Summary

This API map reflects the present system while preparing the structure for future automation, intelligence, and studio-wide operation. Each endpoint is designed to be modular, explicit, and extensible.

