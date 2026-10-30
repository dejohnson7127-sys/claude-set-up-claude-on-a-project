# Notes

## What's in CLAUDE.md, and what I left out

`CLAUDE.md` has a one-line description of the API, the three commands I run most (`npm run dev`, `npm test`, `npm run lint`), a few conventions (one router per file under `routes/`, use `db/store.js` instead of adding a database, explicit JSON status codes), and a short map of which file does what. That's the stuff Claude can't reliably guess and needs at the start of every session.

I left out setup steps, long code examples, and general Express or JavaScript advice. Claude already knows that, or can read it from the code, and every line in `CLAUDE.md` is loaded into every session. Extra text costs context and buries the rules that matter. I also kept secrets and personal preferences out, since the file is committed and shared.

## Permission rules, and what the deny rule prevents

In `.claude/settings.json`:

- **allow:** `npm test` and `npm run lint`. They're safe, read-only checks I run all the time, so they shouldn't prompt.
- **ask:** `git push`, so I can look at a branch before it goes to GitHub.
- **deny:** `Read(./.env)` and `git push --force`.

Without the `.env` deny rule, Claude could read the real `.env` while debugging config. Any secrets in it (database passwords, API keys) would end up in the conversation, could be sent to the model provider, and could get copied into code, logs, or commit messages. Without the force-push deny, one bad command could overwrite commits on `main` that other people depend on, and that is hard to undo.

Deny rules are a backstop, not the main defense. `.env` also has to stay out of git. The `.gitignore` entry was indented with spaces, which made git ignore the rule, so `.env` would have been committed.
