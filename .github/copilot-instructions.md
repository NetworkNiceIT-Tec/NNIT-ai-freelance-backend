# GitHub Copilot instructions for NetworkNiceIT-Tec/NNIT-ai-freelance-backend

**Purpose:** Short, actionable guidance for AI coding agents contributing small bootstraps or fixes to this repository.

---

## Quick summary
- This repo contains small bootstrap examples for different stacks; the `feat/bootstrap-nodejs` branch includes a Node.js example using Express + Jest + Supertest.
- Primary job for agents: propose minimal, focused bootstrap PRs (one small service + tests + CI) or open an issue to clarify requirements before larger changes.

---

## First actions (must do before coding)
1. Inspect the repo root for language manifests and CI config files (`package.json`, `pyproject.toml`, `go.mod`, `Dockerfile`, `.github/workflows/*`).
2. Read `README.md` and `CONTRIBUTING.md` to confirm the preferred workflow for bootstraps and PR size.
3. If a language-specific example already exists in a branch (e.g., `feat/bootstrap-nodejs`), read those files to copy local patterns (see `src/index.js`, `test/health.test.js`).
4. For non-trivial changes open an issue describing design and constraints and wait for maintainers to confirm before implementing.

---

## Concrete project patterns (Node.js example)
- Package scripts:
  - `start` -> `node src/index.js`
  - `test` -> `jest --runInBand` (see `package.json`)
- Test pattern: use `supertest` + `jest` to test an exported Express app. Example files: `src/index.js` (exports app; server started only when run directly) and `test/health.test.js`.
- Keep bootstraps minimal: one small server, one test that demonstrates the pipeline, and a matching `.github/workflows/nodejs.yml` CI workflow.

---

## When proposing a bootstrap or starter PR
- Keep changes small and focused (one service + tests + CI). Example minimal Node.js PR adds: `package.json`, `src/index.js`, `test/health.test.js`, and a simple `nodejs` workflow.
- Include a short PR description with run/test commands and rationale for chosen dependencies.
- Use branch names like `feat/<short-description>` or `fix/<short-description>`.

---

## Tests, build and verification (repo-specific)
- Use `npm install` then `npm test` (Jest configured in `package.json` uses `--runInBand` to avoid test runner worker issues in simple CI jobs).
- The example exports the Express `app` and uses `supertest` to test endpoints — follow that pattern for new services to keep tests fast and isolated.
- Add a GitHub Actions workflow that runs `npm ci` / `npm test` on `pull_request` and `push` to feature branches and `main`.

---

## Conventions & collaboration
- Always open an issue for non-trivial or architectural changes and request human review before merging.
- Keep PRs small and use conventional commit prefixes (`feat:`, `fix:`, `chore:`).
- Avoid large scaffolding or heavy dependencies unless maintainers approve; prefer small, focused additions.

---

## What to include in the PR description (checklist)
- Motivation and brief design notes
- Files added/changed and why
- Local setup and run/test commands (exact `npm` commands used)
- Any open questions for maintainers (e.g., preferred framework or runtime)

---

## Helpful references
- Look at `src/index.js` and `test/health.test.js` for the canonical Node.js pattern in this repo.
- Check `CONTRIBUTING.md` for repository policy on issues and PR size.

---

If you'd like, I can make the PR that updates this file with these repo-specific details, or iterate on wording based on any additional constraints you want documented.
