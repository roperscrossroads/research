# templates

Starting points for research reports. Copy the relevant file into the subject's
directory and fill it in.

| Template | Use for | Lands at |
|---|---|---|
| [`project-summary.md`](project-summary.md) | A structured summary of a project or tool | `<slug>/summary.md` |
| [`security-review.md`](security-review.md) | A public-sources security posture review | `<slug>/security.md` |
| [`qa.md`](qa.md) | A batch of questions with cited answers | `<slug>/qa/YYYY-MM-DD-topic.md` |
| [`comparison.md`](comparison.md) | 2–4 projects compared side by side | `comparisons/<topic-or-projects>.md` |

Each template opens with the required YAML frontmatter (`subject`, `type`,
`title`, `date`, `sources`, `generated-by`) — keep it and fill it in; `INDEX.md`
is generated from it.

To request a report, open an issue from one of the request templates (summary /
comparison / code deep-dive / security review); an agent picks it up and answers
as a pull request.

Every report must follow the scope and citation rules in
[`../AGENTS.md`](../AGENTS.md).
