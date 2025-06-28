# Project Brief: KD Web UI – Modern Replacement for Kindo Desktop

## 🔧 Project Background

This project is a modern, web-based replacement for **KD (Kindo Desktop)**, a legacy WPF/.NET internal tool used by Kindo’s support team. The desktop version currently allows backend operations like:

- Creating users
- Looking up payables
- Enabling/disabling school-level features (e.g. payments, roll)
- Running privileged “SAD” commands for admin-level changes

The current system is command-driven, prone to errors, and difficult for non-technical helpdesk staff to use.

---

## 🎯 Project Goals

### Short-Term
- Build a **lightweight web UI** that focuses only on helpdesk-relevant features
- Create a usable command interface with **dropdown selectors, toggles, and forms** instead of raw strings
- Reproduce KD’s login flow using the `/sessions` API (email + password, returning a session token)

### Long-Term
- Fully replace KD with a secure, browser-based internal tool
- Respect session-based permissioning (including `_sad_` context commands)
- Add modular components (e.g. school picker, config toggles, command previewer)

---

## 🧠 Current State

- The web app uses the `nextjs-boilerplate` template (Next.js 15, App Router, Tailwind CSS, TypeScript)
- The project is managed locally via Cursor
- Source control may be connected to GitHub in future
- Backend calls will mirror the KD command format and endpoint structure (e.g. `/sessions`, `command_exec`)
- There is no need for Clerk or Google login – KD has its own session system

---

## 🧰 Tech Stack

- **Frontend**: Next.js (App Router), Tailwind CSS, TypeScript
- **Session Auth**: Custom login form calling `POST /sessions`
- **Command Execution**: Session-aware POSTs replicating KD behavior
- **State Management**: React state/hooks (no Redux or external store unless needed)

---

## 🧑‍💻 Developer Instructions

You are ChatGPT inside Cursor, acting as a full-stack AI pair programmer. Here’s how you can help:

### 🔍 Legacy Code Understanding
- Help translate WPF/XAML/C# command behaviors into browser-based logic
- Explain what legacy logic is doing and how to adapt it

### 🧱 Component Architecture
- Scaffold reusable UI components:
  - Login form (email + password)
  - Command execution form
  - Context selector (school, supplier, SAD)
  - Roll/payment toggles
- Recommend layout structures using Tailwind

### ⚙️ API & Session Handling
- Replicate KD’s auth flow (store `client_session` token on login)
- Append token to each request using a fetch helper
- Respect `_sad_` context and require PIN/token input

### 📦 Best Practices
- Use TypeScript types/interfaces
- Keep components modular and testable
- Show preview of commands before running them

### 🚫 What Not to Assume
- No third-party auth providers are used
- No backend access — we only call existing APIs
- Developer is a beginner — please explain when needed

---

## ✅ First Tasks

1. Set up the login page and authenticate against `/sessions`
2. Store and reuse session token securely
3. Build basic dashboard layout with:
   - School selector
   - Context switcher (general, school, supplier, `_sad_`)
   - Toggle switches for features
   - Command preview log

---

**Keep this file updated as the project evolves.**
