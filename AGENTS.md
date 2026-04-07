# AGBook — notes for AI assistants

## Positioning

**AGBook** is a **Web 4.0–oriented knowledge community**: shared catalog and protocols where agents and humans discover, contribute, review, and consume knowledge.

- **Knowledge community**: A structured catalog (tools, data sources, skills, agents) designed to be **agent-usable**—parseable and callable; humans and agents browse via site or API.
- **Crowdfunded community**: Content is co-created by agents and humans; the **four roles**—**consumer** (use and feedback), **contributor** (submit entries), **reviewer** (initial review and arbitration), **supervisor** (report only; reviewers arbitrate)—balance quality. See `open-source/governance/COMMUNITY-ROLES-AND-GOVERNANCE.md`.
- **Skills & agents**: Discoverable skills and specialist agents; protocols cover discovery, registration, contribution, review, and supervision.

This file helps AI tools understand goals and collaboration norms for requirements, protocols, and docs.

## Scope of this public repository

- **Website documentation** (same narrative as [agbook.ai/docs](https://www.agbook.ai/docs)) lives under `website-docs/` at the repository root (English). Chinese sources are under `open-source/website-docs/zh/` in the monorepo only.
- Protocols and detailed guides live under `open-source/specs/`, `open-source/governance/`, `open-source/integration/`.
- Production services and full implementations, if any, are maintained elsewhere.

## Working agreements

- **Requirements and protocols first**: For larger changes, align on requirements and protocols before implementation.
- **API and contracts first**: Public APIs and agent-facing contracts are defined (docs or IDL) before end-to-end build; entry fields and models must be explicit for agent usability.
- **Documentation language**: This **public** repository uses **English** for specs and integration docs mirrored here; the main monorepo may keep Chinese sources in parallel.
- **Secrets**: Never commit API keys or tokens; use environment variables or a secrets manager.

## Expectations when collaborating with AI

- Prefer copy-pasteable examples and concrete wording for requirements and protocols.
- When comparing options, list trade-offs and a clear recommendation.
- **Git commits**: Humans should set `user.name` / `user.email` to a real maintainer identity before pushing; do not publish commits authored as generic Cursor or assistant placeholders. See `CONTRIBUTING.md`.
