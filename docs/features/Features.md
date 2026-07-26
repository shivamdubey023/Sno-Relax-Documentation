# ✨ Features

This document describes the core features of **SNO-RELAX**.  
Each feature is presented with a concise explanation suitable for **academic evaluation**, **system understanding**, and **project defense**.

---

## 1. 🤖 AI Chatbot

The AI Chatbot provides conversational, non-clinical mental wellness guidance.

- **External NLP Integration:** Leverages advanced NLP services (e.g., Cohere).
- **Multi-Modal Support:** Supports text-based interaction and limited voice input.
- **Dependency Avoidance:** Designed explicitly to avoid creating dependency on AI.
- **Guidance Over Diagnosis:** Offers suggestions and coping strategies without making medical diagnoses or authoritative claims.

> **Note:** AI usage is explicitly disclosed in the user interface to maintain transparency and user trust.

---

## 2. 📊 Mood Tracking

The Mood Tracking module enables users to log their emotional state over time.

- **Daily Logs:** Easy-to-use daily mood entry functionality.
- **Visual Analytics:** Visualization of mood history using intuitive charts and summary cards.
- **Pattern Identification:** Weekly and monthly averages to help users identify emotional patterns.
- **Contextual Insights:** Mood bands are used to adapt UI hints and provide contextual insights based on user state.

> **Note:** This feature helps users understand overarching trends rather than focusing on isolated emotions.

---

## 3. 💬 Community Groups

Community Groups allow users to interact and share experiences in a controlled, supportive environment.

- **Group Flexibility:** Support for both public and private group spaces.
- **Rich Interactions:** Post creation and threaded replies for deep conversations.
- **Safety Controls:** Comprehensive moderation tools and reporting mechanisms.
- **Live Sync:** Real-time updates for new content, ensuring a lively community.

> **Note:** Safety and respectful interaction are prioritized through stringent moderation controls.

---

## 4. 📄 Hospital Report Summarization

This feature assists users in understanding uploaded medical documents.

- **Secure Handling:** Secure upload and processing of health reports.
- **AI-Assisted Summarization:** Simplifies clinical content to improve readability and comprehension.
- **Consent-Driven Storage:** Summaries are stored only with explicit user consent.

> **Warning:** The system does **not** interpret or diagnose medical conditions under any circumstances.

---

## 5. 🛠️ Admin Panel

The Admin Panel provides robust tools for system oversight and moderation.

- **User & Content Management:** Streamlined user management and content moderation capabilities.
- **Monitoring:** Proactive community and report monitoring.
- **System Configuration:** Platform configuration, analytics, and server-configured fallback theme management.

> **Note:** The admin interface is fully responsive and accessible on both desktop and mobile devices.

---

## 6. 🎨 Theme System

SNO-RELAX includes a global theming system to ensure accessibility and visual consistency.

- **Supported Modes:**
  - **Brand:** Application Default
  - **Dark:** For low-light environments
  - **Light:** For high contrast
- **Unified Context:** Implemented via a single global `ThemeContext`.
- **Persistent Selection:** Theme preferences persist seamlessly across sessions.
- **Instant Propagation:** Theme changes propagate instantly across all pages without requiring a reload.

> **Note:** This design ensures a highly predictable and unified user experience.

---

## 7. 📝 Therapist Notes & Messaging

This module supports private reflections and message-based interaction.

- **Optimistic UI:** Provides immediate visual feedback for message sending.
- **Resilience:** Background retry logic gracefully handles transient network failures.
- **Clear Feedback:** Users receive clear indications of message delivery status.

> **Note:** The system prioritizes responsiveness and resilience to ensure seamless communication.

---

## 8. 🎮 Games & Engagement Features

Lightweight engagement features are included to enhance usability and interaction.

- **Mini-Games:** Simple games (e.g., Tic-Tac-Toe).
- **Stress Relief:** Used primarily for engagement testing and immediate stress relief.
- **Balanced Design:** Designed to complement, not distract from, the core wellness features.

---

## 🛡️ Privacy, Accessibility, and Ethics

- **Privacy First:** User privacy is respected and protected across all features.
- **Transparent AI:** AI involvement is always clearly disclosed.
- **Inclusive Design:** Accessibility considerations are rigorously applied in UI design.
- **Strict Boundaries:** **No feature performs medical diagnosis or autonomous decision-making.**

---

> These features collectively support the academic objectives of the **SNO-RELAX Final Year Project** by demonstrating applied knowledge of modern web development, ethical AI usage, and user-centered design.
