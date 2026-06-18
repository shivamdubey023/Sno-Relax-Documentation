# Technology Stack

This document outlines the technologies used in **SNO-RELAX** and the rationale
behind their selection. The chosen stack balances **research flexibility**,
**scalability**, and **ease of evaluation**, making it suitable for an
undergraduate Final Year Project.

---

## Frontend Technologies

- **React (Create React App)**  
  Used for building both the Client and Admin user interfaces. React enables
  a component-based architecture, efficient state management, and reusable UI
  components.

- **Tailwind CSS / Custom CSS**  
  Provides responsive utility-first styling alongside custom CSS variables for
  global theming and accessibility support.

- **Chart.js**  
  Used for visualizing mood trends and analytics through charts and summary
  components.

---

## Backend Technologies

- **Node.js & Express.js**  
  Form the core backend server, providing RESTful APIs, request handling,
  authentication, and business logic.

- **Socket.IO**  
  Enables real-time communication for chat messages, community updates, and
  live notifications.

- **Axios / Fetch API**  
  Used on the frontend for reliable client–server communication.

---

## Database Technology

- **MongoDB (with Mongoose)**  
  A document-oriented database used to store user profiles, mood logs, messages,
  community data, reports, and system settings. Mongoose provides schema
  validation and data modeling support.

---

## AI and Logic Layer

- **Cohere (Cloud-Based NLP Service)**  
  Used for conversational AI responses and health report summarization.
  AI outputs are mediated by the backend to ensure ethical and controlled usage.

- **Python Scripts**  
  Used for offline experimentation, data preprocessing, and training workflows.
  These scripts support reproducibility and research-oriented extensions.

---

## Development Tools & Environment

- **Git & GitHub**  
  Used for version control, collaboration, and academic submission tracking.

- **Jest / React Testing Library**  
  Support unit and integration testing for frontend components.

- **ESLint / Prettier**  
  Enforce consistent code quality, formatting, and maintainability.

---

## Rationale for Technology Selection

The selected technology stack:
- Supports modular and scalable application design
- Enables ethical and controlled AI experimentation
- Facilitates real-time features with minimal complexity
- Is well-supported, documented, and suitable for academic evaluation

---

This technology stack aligns with the objectives of the **SNO-RELAX Final Year
Project**, ensuring reliability, reproducibility, and clarity for evaluators and
future researchers.
