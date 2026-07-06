---
repo: gastownhall/beads
url: https://gastownhall.github.io/beads/
summary: Dolt-backed distributed graph issue tracker giving coding agents persistent, dependency-aware memory.
categories: [issue-tracker, agent-memory, developer-tools]
features: [dependency-graph, ready-detection, atomic-claim, injectable-memory, hash-ids-zero-conflict, compaction, dolt-sync, agent-setup]
tags: [go, dolt, cli]
status: adopted
interest: [agent-memory, issue-tracking]
watch_last_release: v1.1.0
watch_last_commit_seen: ""
watch_stars: 25097
---

# gastownhall/beads

`bd` — a Go CLI over a Dolt (version-controlled SQL) database that replaces
markdown TODOs with a dependency-aware task graph for agents: `bd ready`, atomic
claim, `bd remember`/`bd prime` injectable memory, hash IDs for conflict-free
multi-agent work, and semantic compaction. By Steve Yegge. MIT, ~25k★. Substrate
for gastown.

Full report: [`../projects/beads/summary.md`](../projects/beads/summary.md).
