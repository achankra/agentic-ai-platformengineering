***** DO NOT USE THIS REPO. THIS WAS ONLY INTENDED FOR THE JANUARY 2026 COURSE *****

Please use the latest [repo](https://github.com/achankra/agentic-pe-oreilly)

# Course Setup & Prerequisites

This repository is used in the **Agentic AI in Platform Engineering** course, a **1-day (4-hour) instructor-led workshop** combining lectures and live demos.

During the course, all demonstrations are shown live by the instructor.  
**After the course**, participants can fork or download this repository and explore it independently at their own pace.

This document explains the **minimum setup required** and the **tools used in the course**.

---

## 1. Required Accounts & Tools (Free Tier)

### GitHub (Required)

You will need a **free GitHub account**.

GitHub is used for:
- Forking this repository
- Running and viewing GitHub Actions workflows
- Hosting the demo portal using **GitHub Pages**
- Browser-based editing using **github.dev** or **GitHub Codespaces**

Create an account:  
https://github.com/signup

---

### Claude (Required – Free Tier)

You will need access to **Claude.ai** or **Claude Code** (free tier).

Claude is used for:
- AI-assisted troubleshooting
- Explanations of platform concepts and flows
- Interactive agent-based reasoning tasks
- Lightweight command execution via browser-based terminals (Claude Code)

Claude.ai:  
https://claude.ai

> **Note:** No local LLM installation is required for this course.

---

### Browser-Based Development Environment (Required)

No local IDE is required during the course.

You may use **either**:

- **GitHub.dev**
  - Lightweight, browser-based editor
  - Open any GitHub repository and press `.` (dot)

- **GitHub Codespaces** (optional)
  - Full development environment with terminal access
  - Useful for running commands like `npm` in the browser

Both options work with a free GitHub account (Codespaces has free-tier usage limits).

---

### cURL (Optional)

Used for simple API or endpoint interactions during demos.

Available via:
- Claude Code’s web terminal
- GitHub Codespaces terminal
- Any browser-based CLI environment

No local installation is required.

---

## 2. Repository Usage Model

### During the Course
- The instructor runs all demos live
- Participants follow along conceptually
- No cloning or local setup is required during the session

### After the Course
Participants can:
- Fork this repository
- Clone it locally **or**
- Open it in GitHub.dev or Codespaces
- Experiment with the architecture, agents, and workflows

---

## 3. Technology Stack Overview

This project is intentionally **simple, modern, and browser-friendly**.

### Frontend Framework
- **React + TypeScript** (All of the required code is provided)
- Built using **Vite** for fast builds and simple configuration

### Build Tooling
- **Vite**
  - Fast development server
  - Optimized production builds
  - Static output suitable for GitHub Pages

### Package Management
- **npm**
  - Installs dependencies
  - Runs build and deployment scripts

Deep npm knowledge is **not required** for this course.

**Alternate Technology Stack Overview**

As an added bonus, we are also sharing with you an alternate way to learn with Python. This is not required for you to learn unless you are looking for a python based approach. We will discuss this in the class, but for efficiency won't deep dive. Note that if you use that version of the demo code, you wil lnot be able to deploy or host it anywhere. We recommend that even if you are using this, you first try out the Vite way of doing it before doing the Python approach.


---

## 4. Static Site Hosting (GitHub Pages)

The demo portal can be hosted using **GitHub Pages**. For the class, instructor will show a live version of this for the dynamic nature of the conversation and stability, so that we do not break the portal during the class.

Key characteristics:
- Static site (no backend runtime)
- Production assets live in the `gh-pages` branch
- Publicly accessible URL
- Suitable for internal developer portals and demos

Participants may host their own forked version using the same approach.

---

## 5. Optional Local Setup (Post-Course)

If you want to run the project locally after the course:

### Prerequisites
- Node.js (LTS recommended)
- npm (included with Node.js)

### Commands

Install dependencies:
```
npm install
np run dev
npm run build
npm run deploy
```

## 6. What This Course Is (and Is Not)

### This Course Is:
- A **conceptual + practical** introduction to Agentic AI in Platform Engineering
- Focused on **architecture, workflows, and decision-making**
- Designed to be **tool-agnostic and transferable**

### This Course Is Not:
- A deep React or frontend framework course. You do not need React or frontend experience
- A local environment setup workshop
- A production-grade AI platform implementation. While the agents we build can be scaled, the course itself won't do the required NFRs to make that happen due to the amount of time available.

---

## 7. Support & Exploration

This repository is designed to be:
- Safe to explore
- Easy to modify
- Suitable for experimentation after the course

Participants are encouraged to:
- Fork the repository
- Modify and extend it
- Experiment with flows and agents
- Use Claude to ask **“what if?”** questions

---

Enjoy exploring Agentic AI patterns in Platform Engineering.
