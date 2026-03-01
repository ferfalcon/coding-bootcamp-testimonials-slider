# ChatGPT Project Instructions — Coding bootcamp testimonials slider

These instructions define how ChatGPT should behave and what engineering standards the project must follow.

They are designed to keep the work incremental (“baby steps”), architecture-focused, and portfolio-grade.

---

## Tech baseline

- **pnpm monorepo**
  - `apps/web`: Vite + React + TypeScript
  - `apps/api`: Fastify + TypeScript
  - `packages/shared`: shared types/schemas (runtime validation)

---

## Architecture constraints (must follow)

### Frontend layering
**UI components → view-model hooks → domain → adapters → data sources**

Rules:
- UI must not depend on backend DTO shapes.
- Mapping/transforms belong in adapters.
- Domain stays framework-agnostic (no React imports).

### Backend layering
**routes/controllers → services → repos → DB**

Rules:
- Controllers handle HTTP concerns (status codes, request parsing).
- Services own business rules and decisions.
- Repos abstract persistence (DB details hidden).

### Validation
- Validate at boundaries (API + any external data).
- Prefer **Zod** unless better justified.

---

## Working style (mandatory)

- Work in **baby steps** like humans: small, reversible changes.
- For **EVERY step**, respond using exactly this structure:
  1) Goal (1–2 sentences)
  2) Plan (3–6 bullets)
  3) Code (PASTE-READY full file contents or complete snippets; **NO diffs-only**)
  4) Why (explain every decision + trade-offs + alternatives)
  5) Verify (exact commands + expected result)
  6) Commit suggestion (Conventional Commits)

- Prefer pragmatic implementation first, then tests right after (avoid strict TDD unless requested).
- If you must ask a question, propose a default path and keep moving.

---

## Engineering standards (must-follow)

- **Accessibility is non-negotiable**: keyboard nav, focus management, visible focus, ARIA only when justified.
- Prefer correctness + clarity over cleverness.
- Do not add dependencies unless clearly justified; explain cost + alternatives.
- Always include a verification loop after changes (dev/test/lint/build as relevant).
- Use **Conventional Commits**: `feat/fix/chore/docs/refactor/test`.

---

## Roadmap (guiding)

- **M0**: scaffold monorepo + dev workflow
- **M1**: slider UI (local seed), responsive + accessible
- **M2**: API `GET /testimonials` with validation + consistent errors
- **M3**: wire web ↔ API (loading/error states)
- **M4**: persistence (Prisma + Postgres) + migrations + seed
- **M5**: admin CRUD + auth (JWT) + publish/draft + ordering
- **M6**: production polish (CI, deploy, README + ADRs + architecture diagram)

---

## Documentation expectations

- Maintain `README.md`: setup, scripts, env vars, architecture diagram.
- Add ADRs for meaningful decisions:
  - Context → Decision → Consequences