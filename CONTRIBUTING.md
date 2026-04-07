# Contributing

## Git commit author (no Cursor / editor placeholders)

Use **your own** name and email for commits so GitHub shows the correct maintainer—not a generic Cursor or IDE default.

Before committing in this repo (or in `agbook-open-publish/` after sync):

```bash
git config user.name "Your Name"
git config user.email "you@example.com"
```

For the open mirror only:

```bash
cd agbook-open-publish
git config --local user.name "Your Name"
git config --local user.email "you@example.com"
```

Do **not** leave the author as “Cursor”, “Copilot”, or other assistant placeholders on `git log` / GitHub.

## Contents

Changes to protocols and docs usually start in the private monorepo; run `scripts/sync-open-publish.sh` from the project root, then commit and push here. See `AGENTS.md` in the monorepo for remote URLs and when to push which repository.
