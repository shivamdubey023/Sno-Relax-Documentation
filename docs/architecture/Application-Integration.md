# Application Integration Architecture

This document explains how the core components of **SNO-RELAX**
(Client, Admin, Backend, Database, Real-time services, and AI modules)
are connected and coordinated at runtime.

The focus is on **integration logic**, **state propagation**, and
**communication boundaries**, complementing the System Architecture
and Data Flow documents.

---

## 1. Integration Overview

SNO-RELAX follows a **loosely coupled, centrally coordinated architecture**.

- The **Backend API** acts as the single authoritative integration layer.
- Client and Admin applications never communicate directly with each other.
- Shared concerns (authentication, theme, permissions) are centralized.
- Real-time communication is handled independently via Socket.IO.

This design ensures:
- Predictable behavior
- Easy debugging
- Clear academic explainability

---

## 2. Client ↔ Backend Integration

### REST API Communication
- All CRUD operations use REST endpoints.
- Client communicates with the backend using:
  - JSON over HTTPS
  - Token-based authentication (where applicable)

Examples:
- Mood logging
- Profile updates
- Community content
- Settings persistence

The backend validates all requests before any mutation.

---

## 3. Real-Time Integration (Socket.IO)

### Purpose
To provide instant updates without polling.

### Integrated Features
- Community messages
- Chat updates
- Group notifications

### Design Rules
- Socket events only notify changes
- Actual data consistency is enforced via REST re-fetch or server state
- Socket layer does NOT replace backend authority

This separation prevents real-time logic from corrupting persistent state.

---

## 4. Global State & Cross-Page Consistency

### Theme Integration
- Theme state is mounted at the **application root**
- All pages consume the same theme context
- No page-level theme overrides are allowed

### Navigation & Page Sync
- Navigation does not reset global state
- Profile, Community, Reports, AI Guide, and Admin pages
  all read from shared providers

This ensures:
- Instant theme updates
- Predictable UI behavior
- No partial re-renders

---

## 5. Client ↔ AI Integration

### AI Access Pattern
- Client never calls AI services directly
- All AI requests go through the Backend

### Responsibilities
- Backend:
  - Sanitizes input
  - Applies safeguards
  - Controls AI output
- Client:
  - Displays responses
  - Never treats AI output as authoritative

This protects:
- User safety
- Academic ethics requirements
- System integrity

---

## 6. Admin ↔ System Integration

### Admin Access Model
- Admin application uses the same backend
- Elevated permissions are enforced server-side
- Admin actions:
  - Do not bypass validation
  - Do not modify client logic directly

Admin changes (e.g., theme defaults, moderation)
are reflected across the system via:
- Shared configuration
- Real-time notifications (if applicable)

---

## 7. Database Integration Strategy

- MongoDB stores the canonical state
- No client-side state is treated as permanent
- Writes are validated and version-safe
- Reads are optimized for UI rendering

This supports:
- Safe retries
- Idempotent operations
- Predictable recovery from failures

---

## 8. Failure Handling & Recovery

### Client-Side
- Optimistic updates with rollback
- Graceful error messages
- Retry mechanisms

### Server-Side
- Idempotent mutations
- Input validation
- Controlled AI failures (fallback responses)

---

## 9. Academic & Design Rationale

This integration architecture was chosen to:
- Avoid tight coupling between modules
- Maintain explainable system behavior
- Prevent AI overreach
- Support incremental feature evaluation
- Enable reproducibility during academic review

---

                    ┌──────────────┐
                    │     User     │
                    └──────┬───────┘
                           │
                           ▼
                ┌────────────────────┐
                │   Client Interface │
                │ (Web / Admin UI)   │
                └──────┬───────┬─────┘
                       │       │
                       │       │
        Mood Data,     │       │ Chat Messages,
        Posts, Files   │       │ Report Content
                       │       │
                       ▼       ▼
        ┌────────────────┐     ┌──────────────────┐
        │  Backend API   │     │   AI Processor   │
        │ (Auth, Logic)  │◀── │ (Cohere / NLP)   │ 
        └──────┬────────┘      └─────────┬────────┘
               │                      │
               │                      │
               ▼                      │
     ┌──────────────────┐             │
     │   MongoDB        │             │
     │ (Users, Moods,   │             │
     │ Posts, Reports)  │             │
     └──────────────────┘             │
               ▲                      │
               │                      │
               └──────────Socket.IO───┘
                       (Real-time Updates)

---

                ┌──────────────────────┐
                │   Admin UI (Vercel)  │
                │ Moderation / Safety  │
                └───────────▲──────────┘
                            │
                     Therapist Notes


---

## Summary

The integration architecture of SNO-RELAX ensures that:
- Each component has a clear responsibility
- All communication paths are controlled and auditable
- Global behaviors (theme, auth, state) remain consistent
- The system remains scalable, secure, and academically defensible
