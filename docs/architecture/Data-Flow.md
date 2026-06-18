# Data Flow Diagram (DFD) – SNO-RELAX

This document describes the logical **Data Flow Diagram (DFD)** for the
SNO-RELAX system.  
It explains how data moves between external entities, processes, data stores,
and AI services, supporting academic evaluation and reproducibility.

---

# Level-0 DFD (Context Diagram)

This shows the entire SNO-RELAX system as one process.

---

                ┌──────────────┐
                │     User     │
                └──────┬───────┘
                       │
      Mood, Chat,      │  Responses, Insights,
      Posts, Reports   │  Summaries, Updates
                       │
                ┌──────▼───────┐
                │              │
                │  SNO-RELAX   │
                │   SYSTEM     │
                │              │
                └──────┬───────┘
                       │
        AI Requests     │  AI Responses
                       │
                ┌──────▼───────┐
                │  AI Service  │
                │ (Cohere/NLP) │
                └──────────────┘

---

## External Entities
- User
- AI Service (Cohere or local NLP model)

---

## Data Stores
- MongoDB Database (Users, Moods, Posts, Reports, Settings)

---

## 1. Mood Logging Flow

### Purpose
To record user mood entries and synchronize updates across active sessions.

### Flow
1. User submits a mood entry via the Client interface.
2. Client sends mood data to the Server.
3. Server validates the request (authentication and data format).
4. Mood entry is persisted in the MongoDB database.
5. Server emits a real-time Socket event to notify active client sessions.
6. Client updates the UI optimistically and reconciles with the server response if required.

### Key Characteristics
- Optimistic UI updates  
- Real-time synchronization  
- Safe retry handling  

---

## 2. Chatbot Interaction Flow

### Purpose
To provide AI-assisted, non-clinical conversational guidance.

### Flow
1. User sends a message through the Client chatbot interface.
2. Client forwards the message to the Server AI endpoint.
3. Server sends the request to the AI service (e.g., Cohere).
4. AI service generates a response.
5. Server optionally enriches the response (context, summaries, safeguards).
6. Server returns the final response to the Client.
7. Client renders the message and optionally stores chat history.

### Key Characteristics
- AI used strictly as a guidance layer  
- No medical diagnosis or autonomous decision-making  
- Stateless or minimally stateful processing  

---

## 3. Community Posting Flow

### Purpose
To enable user participation in moderated community discussions.

### Flow
1. User creates a community post in the Client.
2. Client sends post data to the Server.
3. Server validates and stores the post in the database.
4. Server emits a Socket event to subscribed community members.
5. Connected clients receive the update and refresh content as needed.

### Key Characteristics
- Real-time broadcast updates  
- Scalable publish–subscribe model  
- Server-side validation for content integrity  

---

## 4. Health Report Summarization Flow

### Purpose
To summarize uploaded health reports using AI assistance.

### Flow
1. User uploads a health report file via the Client.
2. Client securely uploads the file to the Server.
3. Server sanitizes and processes the uploaded data.
4. Relevant content is forwarded to the AI summarization service.
5. AI returns a summarized output.
6. Server stores the summary only with explicit user consent.
7. Client receives and displays the summarized report.

### Key Characteristics
- Secure file handling  
- Explicit user consent  
- AI used strictly for summarization  

---

## Data Integrity and Reliability

- Optimistic UI patterns are applied where appropriate (e.g., mood logging, messaging).
- Retry mechanisms handle transient failures.
- Server-side mutations are designed to be idempotent where feasible.
- Real-time updates are reconciled with authoritative server state.

---

## Academic Considerations

- All data flows are designed for explainability and predictability.
- AI components are clearly isolated from core system logic.
- The architecture avoids opaque or autonomous AI decision-making.
- Each flow can be independently evaluated and reproduced.

---
# Level-1 DFD

This expands SNO-RELAX into internal processes.

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
        ┌────────────────┐   ┌──────────────────┐
        │  Backend API   │   │   AI Processor   │
        │ (Auth, Logic)  │◀──│ (Cohere / NLP)   │
        └──────┬────────┘   └─────────┬────────┘
               │                          │
               │                          │
               ▼                          │
     ┌──────────────────┐               │
     │   MongoDB        │               │
     │ (Users, Moods,   │               │
     │ Posts, Reports)  │               │
     └──────────────────┘               │
               ▲                          │
               │                          │
               └──────────Socket.IO───────┘
                       (Real-time Updates)


---

## Summary

This DFD demonstrates how SNO-RELAX ensures:
- Controlled data movement
- Ethical AI integration
- Real-time yet consistent state updates
- Scalability and reliability

The data flow design aligns with the academic objectives of the
**SNO-RELAX Final Year Project**.
