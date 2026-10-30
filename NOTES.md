I kept `CLAUDE.md` brief and project-specific: a one-line description, the three commands I use most often, a couple of concrete conventions, and a short architecture summary. I intentionally left out installation history, long examples, or one-off notes because they do not help on this small Express app and would add noise.

The shared permission rules allow the test and lint commands that I use regularly, and they deny access to secrets in `.env` plus force-pushes to GitHub. Those guardrails help prevent accidental leaks or destructive actions. I also set `git push` to ask for confirmation so a branch can be reviewed before it is published.

This setup is meant to keep Claude grounded in the repo structure and to prevent mistakes that are easy to make on a real project.
