# topics

Research that isn't about a single project — concepts, patterns, and questions
that span (or don't belong to) any one repo. For example: "how QUIC hole-punching
works", "OCI supply-chain signing patterns", "comparing consensus algorithms".

```
topics/<slug>/
├── summary.md              # an explainer on the topic
└── qa/
    └── YYYY-MM-DD-topic.md # questions with cited answers
```

Same templates and frontmatter as [`../projects/`](../projects/); these reports
are indexed into [`../INDEX.md`](../INDEX.md) too. Use `projects/` when the
subject *is* a specific repo; use `topics/` when it isn't.
