# GitHub Copilot instructions for NetworkNiceIT-Tec/NNIT-ai-freelance-backend

**Purpose:** Short, actionable guidance for AI coding agents contributing small bootstraps or fixes to this repository.

---

## Quick summary
- This repo is intended to host small bootstrap examples for different stacks. A Node.js example exists in branches used by maintainers; agents should either propose a minimal bootstrap or open an issue to confirm the desired stack.
- Primary job for agents: propose minimal, focused bootstrap PRs (one small service + tests + CI) or open an issue to clarify requirements before larger changes.

---

## First actions (must do before coding)
1. Inspect the repo root for language manifests and CI config files (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Dockerfile`, `Makefile`, `.github/workflows/*`).
2. Read `README.md` and `CONTRIBUTING.md` to confirm the preferred workflow for bootstraps and PR size (if missing, suggest adding them as part of a bootstrap PR).
3. If a language-specific example already exists in a branch (e.g., `feat/bootstrap-nodejs`), read those files to copy local patterns (see `src/index.js`, `test/health.test.js`).
4. For non-trivial changes, open an issue describing design and constraints and wait for maintainers to confirm before implementing.

---

## Bootstrap examples (per-stack guidance)

### Node.js (recommended pattern)
- Files to add: `package.json`, `src/index.js`, `test/health.test.js`, `.github/workflows/nodejs.yml`.
- Scripts:
  - `start` -> `node src/index.js`
  - `test` -> `jest --runInBand`
- Test pattern: use `supertest` + `jest` to test an exported Express `app`. Export the `app` from `src/index.js` and start the server only when run directly (module check).
- CI: run `npm ci && npm test` on `pull_request` and `push` to `main`.

### Python (FastAPI / pytest example)
- Files to add: `pyproject.toml` or `requirements.txt`, `src/app.py` (FastAPI app), `tests/test_health.py`, `.github/workflows/python.yml`.
- Recommended tooling: `pytest` for tests, `httpx` + `pytest-asyncio` for endpoint testing, `uvicorn` for running locally.
- Example test pattern: import the FastAPI `app` and use `TestClient` from `starlette.testclient` or `httpx.AsyncClient` for async tests.
- CI: run `pip install -r requirements.txt && pytest` (or `pipx`/`venv` depending on workflow).

### Go (minimal module example)
- Files to add: `go.mod`, `cmd/server/main.go` (minimal HTTP handler), `internal/` or `pkg/` packages, `*_test.go` tests, `.github/workflows/go.yml`.
- Recommended test pattern: `go test ./...` and simple `net/http/httptest` based handler tests.
- CI: run `go test ./...` and `go vet` as part of workflow.

---

## When proposing a bootstrap or starter PR
- Keep changes small and focused (one service + tests + CI). Example minimal PR for each stack should include a README excerpt, minimal app, one test, and a matching CI workflow.
- Provide a short PR description with run/test commands and rationale for chosen dependencies.
- Use branch names like `feat/bootstrap-<stack>` or `feat/<short-description>`.

---

## Tests, build and verification
- Example commands by stack:
  - Node.js: `npm ci` && `npm test`
  - Python: `pip install -r requirements.txt` && `pytest`
  - Go: `go test ./...`
- Ensure CI jobs run tests on `pull_request` and `push` to `main`.
- Keep tests fast and isolated; for HTTP apps, import the app object and use test clients instead of starting network servers when possible.

---

## Conventions & collaboration
- Open an issue for non-trivial or architectural changes and request maintainers' confirmation before merging.
- Keep PRs small and use conventional commit prefixes (`feat:`, `fix:`, `chore:`).
- Avoid heavy dependencies or large scaffolding without approval — prefer small, focused additions.

---

## What to include in the PR description (checklist)
- Motivation and brief design notes
- Files added/changed and why
- Local setup and run/test commands
- CI changes and expected outcomes
- Any open questions for maintainers (e.g., preferred framework or runtime)

---

## Helpful references
- Node.js canonical pattern: export the `app` from `src/index.js` and test it with `supertest` in `test/health.test.js`.
- Document new conventions (README/CONTRIBUTING) when adding a bootstrap so future agents and contributors can follow the same patterns.

---

If you'd like, I can now create the minimal bootstrap PRs (Node.js, Python, Go) and add `CONTRIBUTING.md` and a PR template. Tell me whether to open all three PRs now (default license: MIT), or create an issue first to ask maintainers which stack to prioritize.
