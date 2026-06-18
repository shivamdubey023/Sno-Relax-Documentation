# System Architecture

This document describes the high-level system architecture of **SNO-RELAX**.  
It outlines the core components, their responsibilities, and how they interact to deliver a scalable, secure, and explainable mental wellness platform.

The architecture is designed to support **modularity**, **real-time communication**, and **ethical AI integration**.

---

## Architectural Overview

SNO-RELAX follows a **client–server architecture** with real-time capabilities and clearly separated concerns between user-facing features, administrative controls, data persistence, and AI-assisted services.

---

## Core Components

### 1. Client Application (React)
- User-facing web application
- Handles:
  - Mood tracking
  - AI chatbot interactions
  - Community participation
  - Profile and settings management
- Communicates with the backend via REST APIs and Socket.IO
- Implements optimistic UI updates where appropriate

---

### 2. Admin Application (React)
- Administrative interface for platform management
- Handles:
  - User and community moderation
  - Reports and analytics
  - Platform configuration
- Uses the same backend services with role-based access control
- Fully responsive for desktop and mobile usage

---

### 3. Backend API (Express.js)
- Central application server
- Responsibilities:
  - Authentication and authorization
  - CRUD operations for users, moods, posts, and reports
  - Business logic enforcement
  - Validation and sanitization of inputs
- Acts as a gateway between clients, database, sockets, and AI services

---

### 4. Real-Time Communication Server (Socket.IO)
- Enables real-time updates for:
  - Chat messages
  - Community posts
  - Live notifications
- Uses event-based communication
- Ensures consistency between connected client sessions

---

### 5. Database (MongoDB)
- Stores persistent application data:
  - User profiles
  - Mood logs
  - Community posts
  - Chat history (where applicable)
  - System and admin settings
- Schema design prioritizes flexibility and scalability

---

### 6. AI Services
- AI is used strictly as an **assistive layer**
- Responsibilities include:
  - Chat response generation
  - Health report summarization
- Implemented via:
  - External AI APIs (e.g., Cohere)
  - Optional Python-based helpers for offline experimentation or training
- AI outputs are post-processed by the backend before being sent to clients

---

## Interaction Flow (High-Level)

1. User interacts with the Client Application (mood logging, chat, community).
2. Client sends REST API requests to the Backend for standard operations.
3. Real-time events (messages, updates) are transmitted via Socket.IO.
4. For AI-assisted features:
   - Backend forwards requests to the AI service
   - Processes and validates AI responses
   - Returns controlled outputs to the client
5. All persistent data is stored in MongoDB.
6. Admin Application accesses the same backend with elevated permissions.

---

## Configuration & Deployment

- The system supports environment-based configuration.
- Key configuration points:
  - Client API base URL via `REACT_APP_API_BASE`
  - Backend environment variables for:
    - Database connection URIs
    - API keys
    - Security settings
- Backend services and AI integrations can be containerized and deployed independently.

---

## Security Considerations

- Authentication and authorization are enforced server-side.
- Role-based access control separates user and admin privileges.
- Sensitive operations (admin actions, report uploads) require strict validation.
- API keys and credentials are never hardcoded and are managed via environment variables.
- Uploaded files and report data are handled using **privacy-first principles**.

---

## Academic Considerations

- Clear separation between system logic and AI components
- Predictable and explainable system behavior
- No autonomous or diagnostic AI decisions
- Architecture designed for ease of evaluation and reproducibility

---

This system architecture supports the academic goals of the **SNO-RELAX Final Year Project** by combining modern web technologies with ethical AI usage and scalable design principles.
