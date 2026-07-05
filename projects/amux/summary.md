---
subject: amux
type: summary
title: "amux"
date: 2026-07-05
sources: 2
generated-by: research (manual investigation)
---

# amux

> A terminal UI for running multiple coding agents in parallel with a
> workspace-first model, each agent in its own tmux session and Git worktree.

- **Category:** parallel coding-agent workbench (terminal UI)
- **Homepage:** https://github.com/andyrewlee/amux
- **Source:** https://github.com/andyrewlee/amux
- **Docs:** in-repo (`ARCHITECTURE.md`, `CONTRIBUTING.md`, `LINTING.md`)
- **License:** MIT
- **Language / stack:** Go (requires tmux ≥ 3.2; Linux / macOS only)

## Summary

amux is a terminal-based dashboard for launching and managing several coding
agents at once. It uses a workspace-first model — each workspace tracks a repo
checkout, typically backed by a Git worktree on its own branch — and runs each
agent in its own tmux session for isolation and persistence. It is the lightweight,
keyboard-driven cousin of desktop tools like emdash. [1][2]

## Key capabilities

- **Parallel agents** — launch multiple agents in the main repo and within
  separate workspaces. [1]
- **No wrappers** — works directly with Claude Code, Codex, Gemini, Amp,
  OpenCode, and Droid. [1]
- **All-in-one TUI** — run agents, view diffs, and access a terminal from one
  keyboard/mouse-operable interface. [1]
- **Trust-gated project scripts** — a repo's `.amux/workspaces.json` setup/run/
  archive commands are only executed after you explicitly trust the file; editing
  it re-gates the commands. A notable supply-chain safety default. [1]

## Architecture

amux is a Go TUI. Each agent runs in its own tmux session (tmux ≥ 3.2 is a hard
prerequisite) for terminal isolation and persistence across restarts. Workspaces
are the core abstraction: metadata lives under `~/.amux/workspaces-metadata/`,
worktree directories under `~/.amux/workspaces/<project>/<workspace>`, and
trusted-repo script approvals in `~/.amux/trusted-scripts.json`. The repo ships
layered `ARCHITECTURE.md` docs covering PTY flow, tmux tagging, persistence
invariants, and message-boundary discipline — with byte-level PTY tracing
(`AMUX_PTY_TRACE`) for debugging send/receive issues. [1]

## Strengths

- Lightweight and terminal-native — no Electron/desktop footprint; fits a
  keyboard-driven, SSH-friendly workflow. [1]
- Thoughtful safety default: repo-supplied scripts are trust-gated, not executed
  blindly. [1]
- Unusually detailed operational tooling (pprof, profiling, goroutine dumps, PTY
  tracing) for such an early project. [1]

## Limitations / trade-offs

- **Very early / solo project** — v0.0.19, ~130 stars, single maintainer; expect
  churn and gaps versus more established tools. [2]
- **Hard tmux dependency; no Windows support.** [1]
- Same single-machine, human-driven scope as emdash — a workstation tool, not
  server-side automation. [1]

## Alternatives

- **emdash** — the same parallel-agents-in-worktrees concept as a polished
  cross-platform desktop GUI with issue-tracker integrations. [1]
- **Plain tmux + Git worktrees** — the manual pattern amux wraps. [1]

## Notable facts

- Created 2025-12; latest release **v0.0.19** (2026-05-11); ~133 stars — the
  least mature of the three tools reviewed here. [2]
- Requires Go 1.26 with a patched toolchain pinned in `go.mod` for contributors. [1]

## Sources

- [1] https://github.com/andyrewlee/amux — README (how it works, features, configuration, operations)
- [2] https://api.github.com/repos/andyrewlee/amux — repository metadata (stars, license, release, dates)
