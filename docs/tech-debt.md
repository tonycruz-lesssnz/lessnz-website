# Lessnz Tech Debt Audit  
*Structured, Prioritized, and Academically Evaluated*

This audit identifies current limitations, risks, and opportunities for modernization.

---

# 1. Critical (Fix Immediately)

## 1.1 Routing Consolidation  
The current React/Vite routing can become brittle with increasing page complexity.  
**Impact:** UI inconsistencies, navigation edge cases.  
**Fix:** Introduce a routing abstraction or move to Next.js (future).  

## 1.2 Monolithic Express Route File  
`routes.ts` is too large and blends unrelated concerns.  
**Impact:** Harder debugging, slower onboarding.  
**Fix:** Split into domain modules: lessons, assignments, users, media, payments.

## 1.3 Missing Permission Enforcement  
Some endpoints rely on implicit trust rather than explicit ownership checks.  
**Impact:** Security vulnerabilities.  
**Fix:** Implement a centralized authorization middleware.

## 1.4 Media Upload Error Handling  
Uploads lack retry logic and predictable error reporting.  
**Impact:** Student frustration, lost work.  
**Fix:** Harden Uppy + S3 signing workflow.

---

# 2. High Priority (Q1–Q2 2026)

## 2.1 Lack of Service Layer Abstractions  
Business logic is embedded in controllers.  
**Fix:** Introduce domain services (LessonService, AssignmentService, BillingService).

## 2.2 Database Indexing  
Tables need predictable indexes for:
- lessons by teacher  
- assignments by student  
- practice logs by date  

**Fix:** Add indexes + query optimization.

## 2.3 Tests  
Limited test coverage (especially for scheduling + practice logs).  
**Fix:** Introduce Playwright + integration tests.

---

# 3. Medium Priority (Q2–Q3 2026)

## 3.1 Frontend State Management  
React Query handles data well, but UI-level state lacks structure.  
**Fix:** Add Zustand or Jotai for local state.

## 3.2 Performance Considerations  
- Resource-heavy pages  
- Large media preview loads  
- React rendering on heavy dashboards  

**Fix:** Virtualize lists + add component memoization.

---

# 4. Low Priority (Q3–Q4 2026)

## 4.1 Developer Experience  
- Improve folder structure  
- Add lint rules  
- Add architectural guidelines  

## 4.2 Logging & Monitoring  
- Add server logs (winston/pino)  
- Add client analytics (PostHog)  

---

# 5. Future Debt (Post-Next.js Migration)

## 5.1 Serverless Cold Starts  
When moving to serverless, latency must be mitigated.

## 5.2 Widening AI Dependencies  
AI-powered lesson summaries and personalization may balloon compute costs.

---

# Summary
Lessnz is structurally sound for an early-stage SaaS. With incremental cleanup and a clear migration path, it will evolve into a scalable, beautiful, and maintainable music-education platform.

