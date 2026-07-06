---
subject: beads
type: summary
title: "Beads (bd)"
date: 2026-07-05
sources: 3
generated-by: research (manual investigation)
---

# Beads (bd)

> A distributed, dependency-aware graph issue tracker that gives coding agents
> persistent, structured memory — replacing messy markdown plans with a Dolt-backed
> task graph.

- **Category:** issue tracker / agent memory
- **Homepage:** https://gastownhall.github.io/beads/
- **Source:** https://github.com/gastownhall/beads
- **License:** MIT
- **Language / stack:** Go (CLI `bd`; also distributed via npm `@beads/bd` and PyPI `beads-mcp`)

## Summary

Beads (`bd`) provides persistent, structured memory for coding agents. Instead of
tracking long-horizon work in markdown TODO lists that fall out of context, agents
record tasks as nodes in a dependency-aware graph, so blockers, readiness, and
history survive across sessions. It is powered by Dolt — a version-controlled SQL
database — which gives it branching, cell-level merge, and remote sync. [1]

## Key capabilities

- **Dependency graph** — tasks link via `blocks`, `relates_to`, `duplicates`,
  `supersedes`, `replies_to`; `bd ready` surfaces tasks with no open blockers. [1]
- **Agent-optimized workflow** — JSON output, atomic claim (`bd update --claim`),
  and `bd prime` to inject workflow context + persistent memories into an agent. [1]
- **Persistent memory** — `bd remember "insight"` stores project memory that
  `bd prime` re-injects later (a replacement for MEMORY.md files). [1]
- **Zero-conflict multi-agent** — hash-based IDs (`bd-a1b2`) avoid merge
  collisions across parallel agents/branches; hierarchical IDs model epics. [1]
- **Compaction** — semantic "memory decay" summarizes old closed tasks to save
  context window. [1]
- **Turnkey agent setup** — `bd setup claude|codex|factory|cursor|mux…` installs
  the relevant hooks/skills/AGENTS.md guidance. [1]

## Architecture

Beads is a single Go CLI (`bd`) over a Dolt database. Dolt gives it
version-controlled, branchable storage with cell-level merge and built-in sync via
Dolt remotes. It runs **embedded** by default (local Dolt) or against a shared
Dolt **server** for live multi-agent writes. Hash-based IDs and the dependency
graph are what make concurrent, multi-branch agent work merge cleanly. Upgrades can
carry schema migrations, so a remote-synced database is migrated by exactly one
designated clone. [1]

## Strengths

- Purpose-built for agents: readiness detection, atomic claim, JSON, and
  injectable memory map directly onto how agents plan and execute. [1]
- Dolt backing gives real version control, branching, and conflict-free sync —
  unusual for an issue tracker. [1]
- Broad install/integration surface (brew, npm, PyPI; Claude/Codex/Cursor/etc.). [1]

## Limitations / trade-offs

- The Dolt dependency and schema-migration-on-upgrade add operational care
  (back up before upgrading; one clone migrates a synced DB). [1]
- Windows AV false positives are called out, requiring checksum verification. [1]
- Value is highest with agents that actually adopt the workflow; as a plain human
  tracker it's heavier than a flat list. [1]

## Alternatives

- **Plain markdown TODO lists** — what beads explicitly replaces (no dependencies,
  no cross-session memory). [1]
- **Conventional issue trackers (GitHub Issues, Jira)** — human-first, not
  agent-optimized or git-native the way beads is. [1]

## Notable facts

- ~25k GitHub stars; latest release **v1.1.0** (2026-07-04); by Steve Yegge. [2][3]
- It is the work-tracking substrate for **gastown** (also gastownhall), which
  stores multi-agent work state in the beads ledger. [1]

## Sources

- [1] https://github.com/gastownhall/beads — README (features, commands, storage modes)
- [2] https://api.github.com/repos/gastownhall/beads — repository metadata (stars, license, dates)
- [3] https://github.com/gastownhall/beads/releases/latest — latest release v1.1.0 (2026-07-04)
