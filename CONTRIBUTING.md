# Contributing

Thanks for helping! This repo is currently empty; when proposing changes follow these steps:

1. Open an issue describing the change (design, stack, or feature) if it's non-trivial.
2. Create a small, focused branch from `main` with a descriptive name: `feat/...`, `fix/...`.
3. Keep PRs small and easy to review. Include a short description of motivation and design decisions.
4. Include local setup instructions and test commands in the PR description.
5. Use conventional commit prefixes (`feat:`, `fix:`, `chore:`).
6. Add or update `README.md` to document any conventions introduced.

If you're bootstrapping a stack, include at least one CI workflow and one passing test to demonstrate the pipeline.

**Bootstrap specifics (Node.js)**
- Add `engines.node` (>=18) to `package.json` to document the preferred Node version.
- Include a minimal GitHub Actions workflow at `.github/workflows/nodejs.yml` that runs `npm ci` and `npm test`.
- Export the Express `app` from `src/index.js` and write fast tests using `supertest` + `jest` similar to `test/health.test.js`.

**Bootstrap specifics (Python)**
- Prefer FastAPI for HTTP bootstraps. Add `pyproject.toml` or `requirements.txt` with `fastapi`, `uvicorn`, `pytest`, and `httpx` or `pytest-asyncio` for async tests.
- Put the app in `src/app.py` and use `TestClient` or `httpx.AsyncClient` to test endpoints without starting an external server.
- Add `.github/workflows/python.yml` to run `pip install -r requirements.txt && pytest`.

**Bootstrap specifics (Go)**
- Keep modules simple: `go mod init github.com/yourorg/nnit-example` then add `cmd/server/main.go` with a minimal handler.
- Use `net/http/httptest` for handler tests and run `go test ./...` in CI.
- Add `.github/workflows/go.yml` to run `go test ./...` and basic `go vet` checks.

**Checklist for bootstraps**
- Small runnable example with one test and matching CI.
- `README.md` with run/test instructions.
- `LICENSE` (MIT by default) and `.gitignore`.
- Open an issue first for non-trivial choices and request maintainers' approval for heavy dependencies.
