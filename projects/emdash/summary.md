---
subject: emdash
type: summary
title: "Emdash"
date: 2026-07-05
sources: 3
generated-by: research (manual investigation)
---

# Emdash

> An open-source desktop app for running multiple AI coding-agent CLIs in
> parallel, each isolated in its own Git worktree, for developers who want to
> explore several fixes or features at once.

- **Category:** parallel coding-agent workbench (desktop app)
- **Homepage:** https://emdash.sh
- **Source:** https://github.com/generalaction/emdash
- **Docs:** https://emdash.sh/docs
- **License:** Apache-2.0
- **Language / stack:** TypeScript (desktop app; macOS / Windows / Linux builds)

## Summary

Emdash is a local-first desktop application that orchestrates the coding-agent
CLIs you already use — Claude Code, Codex, OpenCode, Gemini, Amp, Copilot and
others — running each task in its own Git worktree and branch so several agents
can work at once without colliding. You review the resulting diffs, open PRs, and
merge what works, all from one window. [1][2]

## Key capabilities

- **Parallel agents** — run multiple coding agents simultaneously, each in an
  isolated Git worktree/branch, instead of juggling terminals. [1]
- **Bring-your-own agent** — auto-detects installed provider CLIs (Claude Code,
  Codex, Cursor, OpenCode, Gemini, Amp, Devin, Qwen Code, Droid, Copilot). [1]
- **Issue-tracker intake** — pull tickets from Linear, GitHub, Jira, GitLab,
  Asana, Featurebase, Monday.com, **Forgejo**, or Plain straight into an agent. [1]
- **Local + remote** — works on local projects or on your own remote machines
  over SSH/SFTP, with credentials in the OS keychain. [1]
- **Review-to-merge in one place** — inspect diffs, create PRs, view CI checks,
  and merge without leaving the app. [1]

## Architecture

Emdash is a cross-platform desktop app (TypeScript, distributed as DMG / MSI /
AppImage / deb). It is a *driver* around external agent CLIs rather than an agent
runtime itself: it detects installed provider CLIs and launches them, giving each
task a dedicated Git worktree and branch. App state lives in a local SQLite
database and, per the project, code and chats are not sent to Emdash's own servers
— the agent CLIs talk to their respective model providers directly. Telemetry is
optional and can be disabled. [1]

## Strengths

- Turns the increasingly common "run several Claude Code sessions in parallel"
  habit into a managed, reviewable workflow. [1]
- Broad provider and issue-tracker coverage, including self-hosted **Forgejo** as
  a ticket source — relevant to a Forgejo-centric workflow. [1]
- Local-first with an explicit privacy stance and optional telemetry. [1]

## Limitations / trade-offs

- **A human-driven desktop GUI**, not a headless/server component — it is a
  workstation productivity tool, not something to wire into a server-side agent
  platform. [1]
- Isolation is per-worktree on one machine (or a remote you own); it is not a
  multi-tenant or scheduled-automation system. [1]
- Real work still runs through whichever agent CLI + model provider you point it
  at, so data-handling depends on that provider, not Emdash. [1]

## Alternatives

- **amux** — same "parallel agents in worktrees" idea as a lightweight terminal
  UI instead of a desktop GUI. [3]
- **Plain Git worktrees + tmux** — the manual pattern emdash productizes. [1]

## Notable facts

- ~5.1k GitHub stars; a Y Combinator W26 company; latest release **v1.1.36**
  (2026-07-01), actively developed. [2]
- Explicitly lists Forgejo among supported issue sources — uncommon for a
  commercial-backed agent tool. [1]

## Sources

- [1] https://github.com/generalaction/emdash — README (capabilities, providers, privacy)
- [2] https://api.github.com/repos/generalaction/emdash — repository metadata (stars, license, dates, YC W26)
- [3] https://github.com/andyrewlee/amux — amux, the TUI alternative in the same category
