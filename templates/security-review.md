---
subject: <slug>
type: security
title: "<Project Name> — security review"
date: YYYY-MM-DD
sources: 0
generated-by: <agent name>
---

# <Project Name> — security review

> A public-sources security posture review: how the project handles security,
> its known weak spots, and what a deployer should harden. Not a pen-test —
> a documentation- and code-based assessment.

- **Project:** <name>
- **Version reviewed:** <version / commit, if scoped>
- **Source:** <repo url>
- **Security docs:** <security policy / advisories url>

## Overview

Two sentences: what the project is and why its security matters (what it
guards, who it's exposed to). [n]

## Security model

- **Authentication** — how identity is established; supported methods (SSO,
  OIDC, local, MFA). [n]
- **Authorization** — how access is scoped (roles, ACLs, multi-tenancy). [n]
- **Data handling** — what data it holds, encryption at rest / in transit,
  secret management. [n]
- **Network exposure** — default listeners, what's meant to be public vs
  internal, TLS defaults. [n]

## Known issues & advisories

- Notable CVEs, security advisories, or widely-reported weaknesses, with dates
  and status (patched in?). Cite the advisory. [n]
- If the project has no published security policy or advisory feed, say so —
  that is itself a finding.

## Secure-by-design questions

The open questions a deployer should answer before trusting this in
production, grouped by theme (Architecture / Authentication / Data / Operations).
Prioritised, one line each. [n]

## Hardening recommendations

- Concrete, cited steps a deployer can take to reduce risk (config flags,
  network placement, disabling defaults). [n]

## Bottom line

A 2–3 sentence verdict: is the default posture safe, and what's the single most
important thing to get right?

## Sources

- [1] <url> — what it is
- [2] <url> — what it is
