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