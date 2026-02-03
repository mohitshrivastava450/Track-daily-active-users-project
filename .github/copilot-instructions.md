<!-- GitHub Copilot instructions for contributors and AI coding agents -->
# Copilot / AI Agent Instructions

Purpose: Help AI coding agents be productive in this repository by documenting structure, developer workflows, and project-specific conventions.

- **Repo type:** Documentation & analytics guide for DAU tracking. Primary content lives in `daily-AI-Usage-Behaviour/` (Markdown-centered analysis, cohort definitions, and implementation checklist).
- **Primary files to edit:**
  - `daily-AI-Usage-Behaviour/Analytical-Guide.md` — canonical analytical playbook; update phases and dashboards here.
  - `daily-AI-Usage-Behaviour/columndescription.md` — schema and field definitions.
  - `daily-AI-Usage-Behaviour/Idea.md` and `Domain&endgoal.md` — product/context notes.

- **Big-picture architecture (what to know):**
  - This project is not a running application — it is a design/analysis repo that documents data flows (users_profiles ↔ sessions_enriched → DAU fact table) and BI/dashboard recommendations.
  - Key data flows are described in `Analytical-Guide.md` Phase 2–3: cleaning → transformation → DAU aggregation → cohorts → retention.

- **Conventions & patterns for edits:**
  - Keep content in Markdown. Follow existing top-level headings (Phase 1..7) and append new sections under the appropriate Phase.
  - Use the same terminology used in the guide: `users_profiles`, `sessions_enriched`, `DAU`, `cohort`, `engagement score`, `churn_30d`.
  - When adding examples or SQL snippets, use fenced code blocks and label them (e.g., "SQL", "python").

- **What an AI agent should do when asked to change analysis/docs:**
  1. Read `daily-AI-Usage-Behaviour/Analytical-Guide.md` fully to locate the phase/section to update.
  2. Make minimal, focused changes: preserve high-level headers and numbering.
  3. Add examples referencing concrete file paths above and avoid introducing unverified runtime claims (no build system or test commands exist in repo).

- **Project-specific notes discovered in the repo:**
  - There is no src/build/test toolchain present — do not propose commands like `npm install` or `pytest` unless the user adds a code subproject.
  - Proposed analytics outputs (Power BI dashboards, cohort matrices) are design artifacts only — when adding implementation instructions, indicate required infra explicitly (e.g., SQL engine, DB connection).

- **Editing & commit guidance (for AI):**
  - Make small commits with descriptive messages: e.g., "docs: add cohort retention SQL example to Analytical-Guide.md".
  - When adding new files under `daily-AI-Usage-Behaviour/`, include a one-line summary at top and update the Table of Contents in `Analytical-Guide.md` if relevant.

- **Examples of quick tasks an AI can do right away:**
  - Add a short SQL snippet showing DAU aggregation using DISTINCT `user_id` per `session_date` in `Analytical-Guide.md` Phase 3.
  - Add a small checklist entry under "Appendix: Implementation Checklist" when proposing new dashboard pages.

- **When you are unsure:**
  - Ask a clarifying question rather than guessing: e.g., "Do you want runnable ETL code added, or only the analytics design?"

If anything here is unclear or you want different formatting or more examples (SQL, sample Power BI outline), tell me what to expand and I'll update this file.
