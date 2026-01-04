# NNIT-ai-freelance-backend

This repository contains small bootstrap examples demonstrating minimal service setups for different stacks. The goal is to provide concise, well-tested starter examples that contributors can adapt.

Current bootstraps (open PRs):

- Node.js (Express + Jest + Supertest) — PR #1, branch: `feat/bootstrap-nodejs`
  - Files: `package.json`, `src/index.js`, `test/health.test.js`, `.github/workflows/nodejs.yml`
  - Run: `npm ci && npm test`

- Python (FastAPI + pytest) — PR #3, branch: `feat/bootstrap-python`
  - Files: `requirements.txt`, `src/app.py`, `tests/test_health.py`, `.github/workflows/python.yml`
  - Run: `pip install -r requirements.txt && pytest`

- Go (minimal HTTP + tests) — PR #4, branch: `feat/bootstrap-go`
  - Files: `go.mod`, `cmd/server/main.go`, `server/health_test.go`, `.github/workflows/go.yml`
  - Run: `go test ./...`

How to help
- Review the PRs above and comment on which stack(s) you'd like to keep or refine.
- If you plan to add a new bootstrap, open an issue first to describe the stack and scope.

License
- MIT (see `LICENSE` files in the bootstrap branches).
