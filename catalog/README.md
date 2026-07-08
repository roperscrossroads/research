# catalog

Machine-readable project records — one file per project, `catalog/<slug>.md`,
with structured frontmatter (see [`../templates/catalog-entry.md`](../templates/catalog-entry.md)).

Each record carries the project's `categories`, `features`, `tags`, `status`,
and `watch_*` freshness fields. The unique key is `repo` (`owner/name`) — one
entry per project.

The per-category **category lists** in [`../categories/`](../categories/) are
**generated** from these records by `scripts/build-catalog.py`; after adding or
editing an entry, run `python3 scripts/build-catalog.py` and include the updated
`categories/` files in the same PR (CI fails if they are stale).

> This directory is public. Only public projects and public metadata belong here.
