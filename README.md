# Full-Stack QA Agent Studio — AI Test Engineering Workbench

A modular, browser-based **Full-Stack QA Engineering Agent** with an interactive UI covering all 9 stages of the Software Testing Life Cycle (STLC) — from requirement analysis and BVA test data generation to Playwright UI/API script generation, defect root-cause triage, impact-based regression selection, and Go/No-Go release reporting.

**Live Demo (GitHub Pages):** `https://prathameshnerkar1111.github.io/full-stack-qa-agent-studio/`

---

## Why I Built This
Modern QA teams spend hours switching between PRDs, Excel test sheets, Playwright scripts, Jira bug templates, and release reports. **Full-Stack QA Agent Studio** unifies all 9 QA workflows into one modular workbench where engineers can toggle only the agents they need, chain context automatically between stages, and export production-ready artifacts (`.csv`, `.json`, `.spec.ts`, `.md`).

---

## 9 Modular QA Agents

| # | Agent Module | What It Does | Exportable Output |
| :-: | :--- | :--- | :--- |
| **1** | **Requirement Analyser** | Extracts sequential `REQ-IDs`, Given-When-Then Acceptance Criteria, and missing edge-case clarification questions | Structured Requirements Table |
| **2** | **Test Case Generator** | Generates Positive, Negative, Edge/Boundary, and UI/UX test cases with priority & traceability | Filterable Table + **CSV Export** |
| **3** | **Test Data Generator** | Produces Equivalence Partitioning & Boundary Value datasets (`valid`, `min`, `max`, `invalid`) | BVA Table + **JSON Fixture** |
| **4** | **UI Testing Agent** | Generates runnable Playwright TypeScript specs using resilient `getByRole`/`getByTestId` locators | Copyable / Downloadable `.spec.ts` |
| **5** | **API Testing Agent** | Generates API validation suites (Playwright `APIRequestContext`, REST Assured, Postman `pm.test`, or cURL) | Copyable Spec + **Postman Collection v2.1 (`.json`)** |
| **6** | **Defect Analyser** | Classifies failed logs into `PRODUCT_BUG`, `SCRIPT_ISSUE`, `FLAKY_TIMING`, or `ENV_DATA_ISSUE` | Root-Cause Triage Card |
| **7** | **Bug Report Generator** | Drafts reproducible, Jira-ready defect tickets with Severity, Priority, Steps, and Expected vs. Actual | Jira Bug Cards |
| **8** | **Regression Agent** | Maps PR diffs / changed modules to Tier 1 (Must Run), Tier 2 (Adjacent), and Tier 3 (Deferred) suites | Impact Table + `--grep` Command |
| **9** | **QA Reporting Agent** | Computes Pass Rate %, Execution Progress, RTM, Defect Summary, and **Go / Conditional Hold / No-Go** verdict | Interactive Sub-Tabs + **Multi-Tab Excel (`.xlsx`)** & RTM `.csv` |

---

## Key Features
- **Modular Feature Selector & Presets:** Select any combination of the 9 agents or use 1-click presets (`Full Pipeline`, `Test Design`, `Automation`, `Triage & Release`).
- **Smart Conditional Inputs:** Context fields (Target URL, API Framework, Stack Trace Logs, PR Diff, Execution Metrics) dynamically appear only when relevant agents are selected.
- **Instant Demo Mode + Live Gemini API Mode:**
  - **Demo Mode (Default):** Works offline with zero API key so reviewers and recruiters can test all 9 agents immediately on GitHub Pages.
  - **Live AI Mode:** Uncheck Demo Mode and enter a Google Gemini API key (`gemini-3.8-flash`, `gemini-4-hydrogen`, or `gemini-3.5-flash-lite`) to run real context-chained LLM pipelines with structured JSON outputs.
- **Built-in Sample Scenarios:** 1-click presets for **FlipMart Checkout**, **NexaBank Transfer**, and **REST API Auth**.
- **Run History & Full Export:** Persists the last 10 runs in `localStorage` and exports the entire pipeline output to `Full_Stack_QA_Agent_Report.md`.

---

## Architecture

```text
User Input (Story / Logs / PR Diff / Metrics)
        │
        ▼
┌────────────────────────────────────────────────────────┐
│            Modular Orchestrator (Browser SPA)          │
│  • Context Chaining (Output of Agent N -> Agent N+1)   │
│  • Structured JSON Enforcement (responseMimeType)      │
└───────┬──────────────────┬───────────────────┬─────────┘
        ▼                  ▼                   ▼
  [Layer 1: Design]  [Layer 2: Automation] [Layer 3: Triage]
  1. Req Analyser    4. Playwright UI      6. Defect Analyser
  2. Test Cases      5. API Validation     7. Jira Bug Gen
  3. BVA Test Data                         8. Regression Tier
                                           9. QA Sign-Off
```

---

## Quick Start & GitHub Pages Deployment

### Run Locally
1. Unzip `full-stack-qa-agent-studio.zip`.
2. Double-click `index.html` to open it in Chrome, Edge, or Firefox (no build step or `npm install` required).

### Deploy to GitHub Pages (2 Minutes)
1. Create a new **Public** repository named `full-stack-qa-agent-studio`.
2. Upload `index.html` and `README.md` to the repository root (`main` branch).
3. Go to **Settings → Pages** → set **Source** to **Deploy from a branch** → select **`main`** (`/ root`) → **Save**.
4. Visit `https://<your-username>.github.io/full-stack-qa-agent-studio/`.

---

## Tech Stack
- **Frontend:** Vanilla HTML5, CSS3, ES6+ JavaScript (Zero-dependency Single-File SPA)
- **AI Engine:** Google Gemini REST API (`gemini-3.8-flash` / `gemini-4-hydrogen` / `gemini-3.5-flash-lite`) with Structured JSON Output
- **Storage & Export:** Browser `localStorage`, Blob Downloads (`.csv`, `.json`, `.spec.ts`, `.md`)

---

## Author
**Prathamesh Nerkar** — Senior Quality Analyst & QA Automation Engineer (Playwright, TypeScript, REST API, BFSI & Retail)
