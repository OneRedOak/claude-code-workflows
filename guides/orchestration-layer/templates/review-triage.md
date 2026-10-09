# Review triage rules

Adapted from the condensed review-and-push excerpt on page 9 of *The Orchestration Layer Playbook*. This is a decision aid, not the complete executable skill. It does not grant permission to push changes or post replies.

## Confidence

- **Human reviewer:** start high. Downgrade only after reading the code and confirming the comment misinterprets it.
- **gstack review:** start medium-high. Upgrade to high when an independent Codex review agrees.
- **Codex challenge:** start medium. A concrete reproduction supports high confidence.
- **CodeRabbit:** start low. Read the code and form an independent judgment; do not upgrade solely because a bot asserted a problem.

## Decisions

| Decision | When to use it |
| --- | --- |
| Act | High confidence, or medium confidence for correctness, security, tests, error handling, or data integrity |
| Skip with a substantive reply | The finding is incorrect or outside the agreed scope |
| Skip without a reply | A style or naming preference where the code is correct |

Record every decision in a triage manifest, including skips. Disagreement is allowed; an unexplained omission is not.

## Working rules

- Read the surrounding code before judging a comment.
- Write the manifest before applying fixes.
- Use a branch and separate commits for logical fixes; do not push directly to main.
- Do not amend commits, force-push, or bypass hooks in this workflow.
- Run the relevant checks and inspect CI after pushing.
- Keep fixes, pushes, and replies within the user's authorized scope.

## Manifest starting point

| Finding/source | Evidence | Confidence | Decision | Rationale | Fix/check |
| --- | --- | --- | --- | --- | --- |
| {comment or finding link} | {code location or reproduction} | {high/medium/low} | {act/skip with reply/skip without reply} | {why} | {commit and validation, if applicable} |

To see how these rules fit into the full workflow, from preflight to CI monitoring, read the [review skill principles](./review-skill-example.md).

[Back to the guide](../README.md)
