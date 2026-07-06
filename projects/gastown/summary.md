---
subject: gastown
type: summary
title: "Gas Town"
date: 2026-07-05
sources: 3
generated-by: research (manual investigation)
---

# Gas Town

> A multi-agent orchestration system that coordinates many AI coding agents
> (Claude Code, Copilot, Codex, Gemini…) with git-backed persistent work state,
> aiming to scale from a handful of agents to 20–30.

- **Category:** multi-agent orchestration / workspace manager
- **Homepage:** https://github.com/gastownhall/gastown
- **Source:** https://github.com/gastownhall/gastown
- **License:** MIT
- **Language / stack:** Go (CLI `gt`)

## Summary

Gas Town is a workspace manager for coordinating multiple AI coding agents working
on different tasks. Its core claim is that agents lose context on restart and
manual coordination breaks down past a handful of agents; Gas Town persists work
state in git-backed storage and adds built-in mailboxes, identities, and handoffs
so multi-agent workflows stay reliable at scale. Work state is stored in a **Beads**
ledger (the same project's issue tracker). [1]

## Key capabilities

- **Persistent worker agents** — "Polecats" have persistent identity but ephemeral
  sessions; identity and work history survive restarts via git-worktree "Hooks." [1]
- **Coordination primitives** — a "Mayor" AI coordinator, per-project "Rigs,"
  mailboxes, and severity-routed escalation (`gt escalate`). [1]
- **Work tracking on beads** — "Convoys" bundle beads assigned to agents;
  `mountain`-labeled convoys get autonomous stall detection for epic-scale runs. [1]
- **Watchdog tiers** — Witness (per-rig lifecycle), Deacon (background supervisor),
  and Dogs (maintenance workers) keep agents healthy. [1]
- **Merge queue** — a per-rig "Refinery" batches completed work and merges to main
  via a Bors-style bisecting queue with verification gates. [1]
- **Session continuation & federation** — "Seance" lets an agent query predecessor
  sessions; "Wasteland" federates work across Gas Towns over DoltHub. [1]

## Architecture

Gas Town (CLI `gt`) organizes a workspace ("Town", e.g. `~/gt/`) into project
"Rigs," each wrapping a git repository and its agents. Worker agents (Polecats) run
in ephemeral sessions but persist identity and work via git-worktree-based Hooks,
with work state recorded in a Beads ledger. A layered control plane — Mayor
(coordinator), Deacon/Witness/Dogs (monitoring), Refinery (merge queue), Scheduler
(dispatch capacity governor), and Escalation — supervises many agents at once. It
is heavily themed (Mad Max vocabulary) but maps onto conventional
orchestration/queue/monitoring concepts. [1]

## Strengths

- Opinionated, batteries-included answer to "how do I run 10–30 coding agents
  without chaos" — coordination, monitoring, merge queue, and escalation are all
  built in. [1]
- Persistent identity + git-backed state directly targets the context-loss problem
  of long-running agents. [1]
- Built on beads, so work tracking is a real dependency graph, not ad-hoc notes. [1]

## Limitations / trade-offs

- Large, elaborate conceptual surface (Mayor/Rigs/Polecats/Convoys/Refinery/…) —
  a real learning curve versus lightweight parallel-agent tools. [1]
- Young and fast-moving; heavy machinery is likely more than small projects need. [1][2]
- Tightly coupled to the beads/Dolt ecosystem. [1]

## Alternatives

- **emdash / amux** — lightweight parallel-agent runners (worktrees) without the
  town-scale coordination, monitoring, or merge-queue layers. [1]
- **Archon** — deterministic per-project *workflows* rather than a standing
  multi-agent town. [1]

## Notable facts

- ~16.4k GitHub stars; latest release **v1.2.1** (2026-06-06); by Steve Yegge,
  sibling project to beads. [2][3]
- "Wasteland" adds a federated, reputation-stamped work market across Gas Town
  instances via DoltHub — an unusually ambitious cross-org coordination idea. [1]

## Sources

- [1] https://github.com/gastownhall/gastown — README (overview, core concepts, architecture)
- [2] https://api.github.com/repos/gastownhall/gastown — repository metadata (stars, license, dates)
- [3] https://github.com/gastownhall/gastown/releases/latest — latest release v1.2.1 (2026-06-06)
