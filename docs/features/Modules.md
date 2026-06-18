# Modules

This document describes the major functional modules of **SNO-RELAX**.
The system is organized into well-defined modules to improve **maintainability**,
**scalability**, and **support academic experimentation**.

Each module has a clear responsibility and interacts with other modules through
well-defined interfaces.

---

## 1. Client Module (`sno-relax-client`)

The Client module is the primary user-facing application.

**Responsibilities:**
- React-based user interface
- User onboarding and authentication flows
- Mood tracking and visualization
- Community interaction (posts, replies, real-time updates)
- AI chatbot client interface
- Health report uploads and result display
- Profile and settings management
- Global theme application via shared theme context

This module communicates with the backend using REST APIs and Socket.IO
and implements optimistic UI patterns where appropriate.

---

## 2. Admin Module (`sno-relax-admin`)

The Admin module provides platform oversight and moderation capabilities.

**Responsibilities:**
- User management and moderation
- Community content review and reporting
- Platform analytics and monitoring
- System configuration and settings
- Server-configured theme fallback management
- Display of admin-only tools and telemetry

The admin interface is implemented using React and is fully responsive
for both desktop and mobile usage.

---

## 3. Server Module (`sno-relax-server`)

The Server module acts as the central coordination layer of the system.

**Responsibilities:**
- REST API endpoints for all core operations
- Authentication and authorization
- Business logic enforcement
- Input validation and sanitization
- Real-time communication via Socket.IO
- Coordination between client, database, and AI services

The server is implemented using Node.js and Express.js and serves as the
single authoritative source of system state.

---

## 4. AI & NLP Module

The AI & NLP module provides assistive intelligence features.

**Responsibilities:**
- Conversational response generation
- Health report summarization
- Controlled AI output processing

**Implementation:**
- External AI services (e.g., Cohere API)
- Optional Python-based utilities for:
  - Offline experimentation
  - Training workflows
  - Data preprocessing

AI usage is strictly assistive and non-clinical, with all outputs
validated and mediated by the backend.

---

## 5. Database Module

The Database module handles persistent data storage.

**Implementation:**
- MongoDB with Mongoose schemas

**Stored Data Includes:**
- User profiles
- Mood logs
- Chat and message records
- Community groups and posts
- Uploaded reports and summaries
- System and admin settings

Schema design prioritizes flexibility, consistency, and scalability.

---

## 6. Shared Utilities Module

The Shared Utilities module contains reusable logic and resources
used across multiple parts of the system.

**Includes:**
- Socket event handlers
- API service helpers
- Theme tokens and CSS variables
- Common UI styles and utilities
- Validation helpers

This module reduces duplication and ensures consistency between
the Client and Admin applications.

---

## Testing and Build Workflows

- Each module supports local development and testing
- Build workflows are configured per module
- Continuous Integration (CI) pipelines are used where configured
- Modular structure allows safe feature toggling and experimentation

---

## Academic Rationale

This modular architecture:
- Encourages separation of concerns
- Supports controlled experimentation
- Simplifies debugging and evaluation
- Enables incremental development and assessment

---

The modular design of **SNO-RELAX** supports both practical implementation
and academic analysis, aligning with the objectives of a **Final Year Project**.
