# Features

This document describes the core features of **SNO-RELAX**.  
Each feature is presented with a concise explanation suitable for **academic evaluation**, **system understanding**, and **project defense**.

---

## 1. AI Chatbot

The AI Chatbot provides conversational, non-clinical mental wellness guidance.

- Integrates with an external NLP service (e.g., Cohere)
- Supports text-based interaction and limited voice input
- Designed to avoid dependency on AI
- Offers suggestions and coping strategies without diagnosis or authoritative claims

AI usage is explicitly disclosed in the user interface to maintain transparency.

---

## 2. Mood Tracking

The Mood Tracking module enables users to log their emotional state over time.

- Daily mood entries recorded by users
- Visualization of mood history using charts and summary cards
- Weekly and monthly averages for pattern identification
- Mood bands are used to adapt UI hints and contextual insights

This feature helps users understand trends rather than focusing on isolated emotions.

---

## 3. Community Groups

Community Groups allow users to interact and share experiences in a controlled environment.

- Public and private group support
- Post creation and threaded replies
- Moderation tools and reporting mechanisms
- Real-time updates for new content

Safety and respectful interaction are prioritized through moderation controls.

---

## 4. Hospital Report Summarization

This feature assists users in understanding uploaded medical documents.

- Secure upload of health reports
- AI-assisted summarization of clinical content
- Summaries are generated to improve readability and comprehension
- Storage of summaries occurs only with user consent

The system does not interpret or diagnose medical conditions.

---

## 5. Admin Panel

The Admin Panel provides tools for system oversight and moderation.

- User management and content moderation
- Community and report monitoring
- Platform configuration and analytics
- Server-configured fallback theme management

The admin interface is responsive and accessible on both desktop and mobile devices.

---

## 6. Theme System

SNO-RELAX includes a global theming system to ensure accessibility and consistency.

- Three supported modes:
  - Brand (Application Default)
  - Dark
  - Light
- Implemented via a single global `ThemeContext`
- Theme selection persists across sessions
- Theme changes propagate instantly across all pages

This design ensures a predictable and unified user experience.

---

## 7. Therapist Notes & Messaging

This module supports private reflections and message-based interaction.

- Optimistic UI for message sending
- Messages appear immediately upon submission
- Background retry logic handles transient failures
- Clear feedback provided on delivery status

The system prioritizes responsiveness and resilience.

---

## 8. Games & Engagement Features

Lightweight engagement features are included to enhance usability and interaction.

- Simple games (e.g., Tic-Tac-Toe)
- Used for engagement testing and stress relief
- Designed to complement, not distract from, core wellness features

---

## Privacy, Accessibility, and Ethics

- User privacy is respected across all features
- AI involvement is clearly disclosed
- Accessibility considerations are applied in UI design
- No feature performs medical diagnosis or autonomous decision-making

---

These features collectively support the academic objectives of the **SNO-RELAX Final Year Project** by demonstrating applied knowledge of modern web development, ethical AI usage, and user-centered design.
