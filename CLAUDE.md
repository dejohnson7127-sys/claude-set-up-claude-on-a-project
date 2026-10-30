# Express user API

Small Express API for serving user data and health checks for local development and testing.

## Commands
- `npm run dev` — start the API on http://localhost:3000
- `npm test` — run the Node.js test suite
- `npm run lint` — check code style with ESLint

## Conventions
- Keep each resource in its own route file under `routes/` and mount it from `server.js`.
- Use `db/store.js` for in-memory data access; do not add a database layer unless the task explicitly requires it.
- Prefer JSON responses and explicit HTTP status codes over implicit fallbacks or silent errors.

## Architecture
- `server.js` is the app entry point and mounts the `/users` and `/health` routers.
- `routes/users.js` handles user listing, lookup, and creation; `routes/health.js` exposes the liveness check.
- `db/store.js` stores the sample user data and the helper functions used by the routes.
- `tests/users.test.js` is the regression suite for the API and should remain the first place to validate changes.
