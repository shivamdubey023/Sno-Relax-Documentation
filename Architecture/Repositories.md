# Repositories

This document provides an overview of the repositories that collectively
form the **SNO-RELAX** Final Year Project.  
Each repository serves a specific role within the overall system and is
maintained independently to support modularity and academic clarity.

---

## 1. Admin Application (`sno-relax-admin`)

- **Repository URL:**  
  https://github.com/shivamdubey023/sno-relax-admin

- **Deployed Application:**  
  https://sno-relax-admin.vercel.app/

- **Purpose:**  
  Provides an administrative interface for moderators and administrators
  to manage users, community content, system configuration, analytics,
  and platform-level controls.

- **Technologies Used:**  
  - JavaScript  
  - React  
  - Socket.IO (client)  
  - Theme-based UI components  

---

## 2. Client Application (`sno-relax-client`)

- **Repository URL:**  
  https://github.com/shivamdubey023/sno-relax-client

- **Deployed Application:**  
  https://sno-relax-client.vercel.app/

- **Purpose:**  
  Implements the user-facing web application, including mood tracking,
  AI chatbot interaction, community groups, health report summarization,
  wellness activities, and global theme management.

- **Technologies Used:**  
  - JavaScript  
  - React  
  - Chart.js  
  - Socket.IO (client)  

---

## 3. Backend Server (`sno-relax-server`)

- **Repository URL:**  
  https://github.com/shivamdubey023/sno-relax-server

- **Purpose:**  
  Acts as the central integration layer of the platform. Responsible for
  authentication, data persistence, community APIs, AI service mediation,
  and real-time communication.

- **Technologies Used:**  
  - Node.js  
  - Express.js  
  - MongoDB (Mongoose)  
  - Socket.IO  
  - External AI APIs (Cohere)  

---

## Integration Focus (Summary)

The SNO-RELAX platform follows a modular, loosely coupled architecture:

- Client and Admin applications communicate only with the Backend server
- The Backend acts as the single source of truth for data and system state
- Real-time features are implemented using Socket.IO without bypassing
  backend validation
- AI services are accessed exclusively through the Backend to maintain
  ethical boundaries and predictable behavior
- Global concerns such as theme management and permissions are centralized

This integration approach ensures clarity, scalability, and academic
explainability across the system.

---

## Maintainers & Contributors

- **Shivam Kumar Dubey**  
  Project Creator and Lead Developer  
  GitHub: https://github.com/shivamdubey023

- **Suryakant Mishra**  
  Co-Creator and Contributor
  GitHub: https://github.com/mishrasuryakant

---

This document is part of the **SNO-RELAX Final Year Project submission**
and is intended for academic reviewers and future maintainers.
