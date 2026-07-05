# AGENTS.md — rules for agents publishing to this repository

This repo is **public**. Any agent that writes here is publishing to the open
internet. Follow these rules exactly.

## Hard scope rules (non-negotiable)

1. **Public sources only.** Research from publicly available project source
   code, documentation, and the web. Do not use any private or internal
   knowledge base as a source.
2. **No infrastructure identifiers, ever.** No hostnames, IP addresses,
   internal DNS names, account IDs, VM/container names, or network topology —
   in file content, file names, or commit messages.
3. **No secrets.** No credentials, tokens, keys, or `.env` content.
4. **No private context.** Nothing about who runs this, where it runs, or how
   it is deployed. If a report only makes sense with private context, it does
   not belong here.
5. **Cite everything.** Every factual claim carries a `[n]` citation to a
   source you actually retrieved. Never fabricate a source or a URL.

A report that cannot satisfy all five rules must not be published.

## How these rules are enforced

The rules above are stated as **principles only** — deliberately. The concrete
list of specific terms and topics that must never appear here is **not kept in
this repository**, because publishing that list would itself expose what it is
meant to protect.

Enforcement happens in three layers:

- **Prompt discipline (primary).** The publishing agent is instructed to work
  only from public sources and to never emit private/infrastructure detail. This
  is the first and most important line — the guardrails below are backstops, not
  a licence to be sloppy in the prompt.
- **A generic pattern scan** any reviewer or CI can run
  (`scripts/trust-tier/scan.sh`, wired to the local hooks and a GitHub Actions
  backstop). It matches only **generic shapes** — RFC1918 addresses, reserved /
  internal DNS suffixes, and secret formats (via gitleaks). It holds **no
  specific domain, hostname, or identifier**, so nothing in this repo ties back
  to any particular network.
- **A private scrub** run by the publishing agent *before* it opens a PR. The
  list of specific strings and excluded topics is **maintained privately,
  outside this repo** — publishing it here would defeat the point. If generated
  output matches, the agent redacts or refuses, and the match never reaches
  public history.

If you are reviewing a PR and something looks like it might be private, treat
that as a blocking question, not a judgement call.

## Layout

One directory per subject (lowercase-kebab slug), plus a top-level
`comparisons/` directory:

```
<project-slug>/
├── summary.md
├── security.md
└── qa/
    └── YYYY-MM-DD-topic.md

comparisons/
└── <topic-or-projects>.md
```

- `<project-slug>` — the project/tool/topic, e.g. `nextcloud`, `paperless-ngx`.
- `summary.md` — one per subject; overwrite/update in place as understanding
  improves.
- `security.md` — one per subject; a public-sources security posture review.
- `qa/YYYY-MM-DD-topic.md` — one file per question batch; append new batches
  rather than editing old ones.
- `comparisons/<topic-or-projects>.md` — a side-by-side of 2–4 projects, named
  for the topic (`self-hosted-file-sync.md`) or the contenders
  (`nextcloud-vs-seafile.md`).

Use the templates in [`templates/`](templates/) verbatim as a starting point.

## Frontmatter (required)

Every report opens with YAML frontmatter so it can be indexed by machine:

```
---
subject: <slug>
type: summary        # summary | qa | comparison | security
title: "<human title>"
date: YYYY-MM-DD
sources: <count>
generated-by: <agent name>
---
```

Do not name specific model versions or internal systems — the agent name is
enough. `INDEX.md` is generated from this frontmatter by
`scripts/build-index.py`; after adding or changing a report, run
`python3 scripts/build-index.py` and include the updated `INDEX.md` in the same
PR. CI fails if the index is stale.

## Delivery

- **One report per pull request.** Branch name: `research/<slug>-<short-desc>`.
- Keep the PR body to a one-line description plus the source count.
- Do not push directly to `main` — it is protected and requires a reviewed PR.

## Contributions & review

`main` is protected: every change lands via a pull request that the maintainer
reviews and merges. Automated contributors (the research agent, GitHub Copilot,
etc.) **open** PRs but never merge their own.

So that the maintainer's review and merge are properly attributed, and so
agent-authored work still counts toward the maintainer's contribution graph,
every agent/Copilot commit **must** carry a co-author trailer:

```
Co-authored-by: roperscrossroads <72768950+roperscrossroads@users.noreply.github.com>
```

(The GitHub `noreply` address is used deliberately — it is linked to the account
and keeps a personal email out of public history.) Agent PRs are merged with the
**merge-commit** option (not squash), so the merge commit is authored by the
maintainer.
