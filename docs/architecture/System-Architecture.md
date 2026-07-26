# 🏗️ System Architecture

This document describes the high-level system architecture of **SNO-RELAX**.  
It outlines the core components, their responsibilities, and how they interact to deliver a scalable, secure, and explainable mental wellness platform.

The architecture is explicitly designed to support **modularity**, **real-time communication**, and **ethical AI integration**.

---

## 🏛️ Architectural Overview

SNO-RELAX follows a **client–server architecture** with real-time capabilities and clearly separated concerns between user-facing features, administrative controls, data persistence, and AI-assisted services.

---

## 🧩 Core Components

### 1. 💻 Client Application (React)
- **Role:** User-facing web application.
- **Responsibilities:**
  - Mood tracking and visualization
  - AI chatbot interactions
  - Community participation and support
  - Profile and settings management
- **Integration:** Communicates with the backend via REST APIs and Socket.IO.
- **UX Strategy:** Implements optimistic UI updates for a seamless experience.

### 2. 🛡️ Admin Application (React)
- **Role:** Administrative interface for platform management.
- **Responsibilities:**
  - User and community moderation
  - Actionable reports and analytics
  - Platform configuration and fallback theme management
- **Integration:** Uses the same backend services secured with role-based access control (RBAC).
- **Accessibility:** Fully responsive for desktop and mobile usage.

### 3. ⚙️ Backend API (Express.js)
- **Role:** Central application server.
- **Responsibilities:**
  - Authentication and authorization
  - CRUD operations for users, moods, posts, and reports
  - Enforcement of core business logic
  - Strict validation and sanitization of inputs
- **Integration:** Acts as a secure gateway between clients, database, sockets, and AI services.

### 4. ⚡ Real-Time Communication Server (Socket.IO)
- **Role:** Real-time event broker.
- **Responsibilities:**
  - Chat message broadcasting
  - Live community posts and updates
  - Instant live notifications
- **Strategy:** Uses event-based communication to ensure state consistency between connected client sessions without bypassing backend authority.

### 5. 🗄️ Database (MongoDB)
- **Role:** Persistent application data store.
- **Data Stored:**
  - User profiles and settings
  - Mood logs
  - Community posts
  - Chat history (where applicable)
  - System and admin configurations
- **Design:** Schema design prioritizes flexibility and horizontal scalability.

### 6. 🤖 AI Services
- **Role:** Intelligent assistive layer (strictly non-diagnostic).
- **Responsibilities:**
  - Contextual chat response generation
  - Health report summarization
- **Implementation:**
  - External NLP APIs (e.g., Cohere)
  - Optional Python-based helpers for offline experimentation
- **Safeguards:** All AI outputs are rigorously post-processed and validated by the backend before reaching the client.

---

## 🔄 Interaction Flow (High-Level)

1. **User Action:** User interacts with the Client Application (e.g., logs mood, chats, posts to community).
2. **API Communication:** Client sends REST API requests to the Backend for standard state-mutating operations.
3. **Live Sync:** Real-time events (messages, status updates) are transmitted via Socket.IO.
4. **AI Mediation:**
   - Backend forwards specific requests to the AI service.
   - Backend processes, sanitizes, and validates AI responses.
   - Returns controlled, safe outputs to the client.
5. **Persistence:** All validated persistent data is securely stored in MongoDB.
6. **Administration:** Admin Application accesses the same backend using elevated credentials to oversee the platform.

---

## 🚀 Configuration & Deployment

- **Environment-Based Config:** The system deeply relies on environment variables to manage environments seamlessly.
- **Key Configuration Points:**
  - Client API base URL via `REACT_APP_API_BASE`
  - Backend environment variables for:
    - Database connection URIs
    - Third-party API keys
    - Cryptographic secrets
- **Containerization Readiness:** Backend services and AI integrations are designed to be container-friendly and deployed independently.

---

## 🔒 Security Considerations

- **Server-Side Validation:** Authentication and authorization are strictly enforced server-side.
- **RBAC:** Role-based access control distinctly separates standard user and administrative privileges.
- **Input Sanitization:** Sensitive operations (admin actions, file uploads) require robust validation.
- **Secret Management:** API keys and credentials are never hardcoded; they are securely managed via environment variables.
- **Data Privacy:** Uploaded files and report data are handled using **privacy-first principles**, prioritizing user consent.

---

## 🎓 Academic Considerations

- **Clear Boundaries:** Unambiguous separation between standard system logic and experimental AI components.
- **Explainability:** Predictable and explainable system behavior suitable for defense.
- **Ethical Safeguards:** Zero autonomous or diagnostic AI decisions.
- **Reproducibility:** Architecture designed explicitly for ease of academic evaluation and environment reproducibility.

---

> This system architecture actively supports the academic goals of the **SNO-RELAX Final Year Project** by intelligently combining modern web technologies with ethical AI usage and scalable design principles.
