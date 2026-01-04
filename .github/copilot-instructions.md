# GitHub Copilot instructions for NetworkNiceIT-Tec/NNIT-ai-freelance-backend

**Purpose:** Provide concise, actionable guidance for AI coding agents working in this repository.

---

## Quick summary
- Current repository state: **no source code detected** (only an image file is tracked). Branch: `main`.
- Primary job for agents: **ask for clarifying requirements or propose a minimal bootstrap plan** before adding substantial code.

---

## First actions (must do before coding)
1. Inspect the repo root for language manifests and CI config files:
   - Look for `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Dockerfile`, `Makefile`, and `.github/workflows/*.yml`.
   - If none exist (as now), **do not** assume a language—open an issue or draft a short proposal PR describing the suggested stack and rationale.
2. Check `README.md` or CONTRIBUTING.md for project goals and conventions. If missing, add a short `README.md` when proposing to bootstrap the project.
3. If asked to implement a feature, **confirm** the required language/runtime and any environment constraints before coding.

---

## When proposing a bootstrap or starter PR
- Keep changes minimal and focused: e.g., add `README.md`, LICENSE, `.gitignore`, and a small `hello-world` service with associated tests and CI.
- Follow these example file choices depending on language:
  - Node.js: `package.json`, `src/`, `test/`, `.github/workflows/nodejs.yml`
  - Python: `pyproject.toml` or `requirements.txt`, `src/`, `tests/`, `.github/workflows/python.yml`
  - Go: `go.mod`, `cmd/`, `internal/`, `.github/workflows/go.yml`
- Include a short PR description describing design choices, run instructions, and how to test locally.

---

## Branching & PR workflow
- Branch from `main` using a descriptive name: `feat/<short-description>` or `fix/<short-description>`.
- Use small, reviewable PRs. Explain assumptions and list commands to run locally.
- Link or open an issue for discussion if the change is architectural or non-trivial.

---

## Tests, build and verification
- If a test framework exists, run its standard command (examples below). If none exist, include tests in the bootstrap PR using a common tool for the chosen language.
  - Node.js: `npm test` or `pnpm test`
  - Python: `pytest`
  - Go: `go test ./...`
- Add a GitHub Actions workflow that runs the tests on `pull_request` and `push` to `main`.

---

## Project-specific conventions & expectations
- No existing conventions are detectable in the repository. When conventions are introduced in a PR, document them in `README.md` and `CONTRIBUTING.md`.
- Use conventional commit prefixes (`feat:`, `fix:`, `chore:`) when creating commits to make changelogs and PR reviews easier.

---

## Safety & collaboration rules (mandatory)
- **Always** open an issue or a draft PR for non-trivial changes and request human review before merging.
- Avoid introducing heavy dependencies or large scaffolding without maintainers' approval.
- When in doubt, ask — prefer a short clarifying issue to speculative implementation.

---

## What to include in the PR description (checklist)
- Motivation and brief design notes
- Files added/changed and why
- Local steps to build/run/test (commands)
- Any open questions for reviewers

---

## Helpful references and next steps for contributors
- If maintainer direction is provided (issue/label), follow it and mention the issue number in the PR.
- If asked to bootstrap the repo, include a minimal CI workflow and at least one passing test to demonstrate the pipeline.

---

### Per-stack guidance & quick examples

Node.js (recommended starter)
- Minimal stack: Node 18+ or 20+, npm or pnpm, Express or Fastify for small services.
- Files to add in a bootstrap: `package.json`, `src/index.js` (Express hello world), `test/` (`jest` or `vitest`), `.github/workflows/nodejs.yml`.
- Example run/test commands:
  - Install: `npm install`
  - Run: `node src/index.js` or `npm start`
  - Test: `npm test` (example Jest command in `package.json`).
- CI note: use `actions/setup-node@v4`, cache `~/.npm` and run `npm test --if-present`.

Python (FastAPI starter)
- Minimal stack: Python 3.11+, `requirements.txt` or `pyproject.toml` (Poetry). Use FastAPI + Uvicorn for small services.
- Files to add in a bootstrap: `pyproject.toml` or `requirements.txt`, `src/app/main.py`, `tests/test_health.py`, `.github/workflows/python.yml`.
- Example run/test commands:
  - Install: `pip install -r requirements.txt`
  - Run server: `uvicorn src.app.main:app --reload --port 8000`
  - Test: `pytest`.
- CI note: use `actions/setup-python@v4`, install with pip, run `pytest -q`.

Go (minimal HTTP service)
- Minimal stack: Go 1.21+, module mode (`go.mod`) and standard `net/http` for example services.
- Files to add in a bootstrap: `go.mod`, `cmd/server/main.go`, `internal/` or `pkg/` for packages, tests `*_test.go`, `.github/workflows/go.yml`.
- Example run/test commands:
  - Build/run: `go run ./cmd/server`
  - Test: `go test ./...`
- CI note: use `actions/setup-go@v4`, `go test ./...` with module caching.

---

#### Examples & patterns to look for when code exists
- API layout: look for `src/controllers`, `api/`, `cmd/` or `internal/` to understand service boundaries.
- Config: prefer environment variables; search for `config`, `.env`, or `env` parsing code to discover required secrets.
- Tests and coverage: check `package.json` or `pyproject.toml` for test scripts and coverage reporters.
- Docker: if a `Dockerfile` exists, prefer using its base image and dev workflow for testing.

---

## CONTRIBUTING & PR templates (what agents should add)
- Add a `CONTRIBUTING.md` with minimal contribution steps and local run/test commands specific to the chosen stack.
- Add `.github/pull_request_template.md` with a concise checklist: motive, design notes, how to run locally, tests added, and any migration/compat notes.

---

If any section is unclear or you want the instructions tailored further, specify the stack(s) and I will update the file with more exact commands, file examples, and CI snippets.