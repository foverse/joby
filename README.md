# Joby

A resume tailoring engine, keyword overlap analyzer, and application pipeline tracker.

- Repository: [https://github.com/foverse/joby](https://github.com/foverse/joby)
- Author: [Fouad](https://growthmaker.fr) ([@foverse](https://github.com/foverse))
- Project Hub: [growthmaker.fr](https://growthmaker.fr)

---

## Overview

Joby adapts a structured Base CV to specific job postings while preserving data integrity. Instead of rewriting experience from scratch, it evaluates keyword coverage, surfaces skill gaps, and generates targeted, single-page outputs without modifying the original baseline.

The application includes an integrated job application CRM to log outreach, set follow-up dates, and maintain application records.

---

## Key Features

### 1. Resume Tailoring Engine
- Immutable Base CV: Keeps your master profile intact while versioning role-specific customizations.
- Versioned Job Snapshots: Captures job description text and hashes to compare iterations over time.
- Literal Keyword Analysis: Flags exact keyword matches, missing terminology, and language requirements.

### 2. PDF Rendering
- Single-page layout enforcement with real-time visual height limits.
- Server-side headless export powered by Puppeteer for exact print rendering.
- Native browser print stylesheet fallback.

### 3. Application Pipeline Tracker
- Kanban and list view for active applications, interviews, offers, and rejections.
- Follow-up date reminders and contact history logging.
- One-click JSON backup export to protect application data.

### 4. Flexible Storage Layer
- Local Mode: Operates completely offline using browser `localStorage` with zero setup required.
- PostgreSQL Mode: Connects to any standard PostgreSQL database (e.g. Aiven, Supabase, Neon) to persist snapshots and tailoring runs across devices.

---

## Tech Stack

- **Frontend:** Vanilla JavaScript, Vite, Modern CSS
- **Backend:** Node.js, Express 5
- **Export Engine:** Puppeteer (Headless Chrome)
- **Database:** PostgreSQL (`pg` pool with TLS support)

---

## Quick Start

### 1. Clone and Install

```bash
git clone https://github.com/foverse/joby.git
cd joby
npm install
```

### 2. Start the Application

Open two terminal tabs:

**Terminal 1 (Vite Dev Server):**
```bash
npm run dev
```

**Terminal 2 (API & PDF Export Server):**
```bash
# Linux/macOS
PORT=3017 npm start

# Windows PowerShell
$env:PORT = "3017"; npm start
```

Open the Vite local address (e.g. `http://localhost:5173`) in your browser.

---

## Environment Configuration

Configuration is optional. By default, Joby runs with zero configuration in local browser storage mode.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `PORT` | API server listening port | `3016` |
| `DATABASE_URL` | PostgreSQL connection string with SSL | None (uses `localStorage`) |
| `AIVEN_DATABASE_URL` | Alternative alias for PostgreSQL connection | None |

When a database connection string is provided, Joby automatically creates the required tables (`joby_base_cv`, `joby_job_snapshots`, and `joby_tailoring_runs`).

---

## Project Structure

```
joby/
â”œâ”€â”€ index.html                  # Main application interface
â”œâ”€â”€ app.js                      # Core state management and tailoring engine
â”œâ”€â”€ applications.js             # Application pipeline CRM and follow-up tracker
â”œâ”€â”€ server.js                   # Express server, Puppeteer PDF generator, and DB layer
â”œâ”€â”€ style.css                   # Core styling and print media rules
â”œâ”€â”€ joby-design.css             # Component styling
â”œâ”€â”€ public/                     # Static assets and icons
â””â”€â”€ package.json                # Project dependencies and run scripts
```

---

## Author

Developed by [Fouad](https://growthmaker.fr).

Explore more tools, case studies, and experiments at [growthmaker.fr](https://growthmaker.fr).
