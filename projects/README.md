# projects

One directory per project, `projects/<slug>/`, holding every report about that
project:

```
projects/<slug>/
├── summary.md              # structured project/tool summary
├── security.md             # public-sources security posture review
└── qa/
    └── YYYY-MM-DD-topic.md # a batch of questions with cited answers
```

The `<slug>` is the project's short name (usually the repo name). The
machine-readable record for each project lives separately in
[`../catalog/`](../catalog/); cross-project comparisons live in
[`../comparisons/`](../comparisons/); research that isn't about a single project
lives in [`../topics/`](../topics/).

Start from the templates in [`../templates/`](../templates/). Every report carries
YAML frontmatter and is indexed into [`../INDEX.md`](../INDEX.md).
