# The Orchestration Layer Playbook

Build the system around Claude Code and Codex that supports longer, more independent work: **context, tools, workflows, and verification**.

**[Download the free PDF](./orchestration-layer-playbook.pdf?raw=1)** · [Tools and resources](./resources.md) · [Copyable templates](./templates/)

No signup required. For practical workflows and hard-won lessons from my journey becoming an AI-native founder, [join my newsletter](https://bhi-patrickellis.beehiiv.com/) (optional).

**Edition:** 1.2 · **Revised:** October 6, 2026 · **Length:** 16 pages · **Author:** Patrick Ellis

## Who this is for

Engineers and founders who already use coding agents and want a repeatable process for giving them context, reviewing their work, and verifying results.

## What's inside

| Pages | Topic |
| --- | --- |
| 2–4 | The shift toward longer tasks and the four-pillar framework |
| 5 | Context inventory and a `CLAUDE.md` starting point |
| 6–7 | Tools, infrastructure context, and scoped permissions |
| 8–9 | Repeatable workflows and review-and-push triage rules |
| 10 | Verification: browser checks, tests, and quality gates |
| 11–12 | An analytics case study and teams of agents |
| 13–14 | Additional field notes and the compounding value of the system |
| 15–16 | A 30-day rollout and the resource directory |

## Start using it

1. Read the four-pillar framework on page 4 and identify the weakest part of your setup.
2. Use the [review triage excerpt](./templates/review-triage.md) to make review decisions explicit, and the [review skill principles](./templates/review-skill-example.md) to see how those rules fit into a full review-and-push loop.
3. Follow the 30-day rollout on page 15, proving one improvement each week.

The PDF explains the workflows and includes adapted examples; it does not include the complete custom `review-and-push`, `sentry-fixes`, or manager-agent implementations shown in the video. Replace example commands and paths with your project's actual checks before using the templates. The triage excerpt and review skill principles are decision aids, not complete installable skills.

## Companion video

Companion to Patrick's video on the four-pillar workflow around Claude Code and Codex. PDF timestamps use elapsed playback time in the **October 5, 2026 evergreen edit (30:54)**, anchored to the existing captions and verified edit map. The direct video link will be added when it is published; find published tutorials on [Patrick Ellis' YouTube channel](https://www.youtube.com/@PatrickOakleyEllis).

## Related workflows

- [Code review](../../code-review/): automate routine PR checks.
- [Security review](../../security-review/): inspect vulnerabilities and security risks.
- [Design review](../../design-review/): review interfaces using browser tooling.

## Revision history

- **1.2 — October 6, 2026:** Clarified that the guide contains workflow explanations and adapted excerpts, not complete custom skill files. Re-anchored all 49 timestamp references to the October 5 evergreen edit. Made the resource-page URLs clickable and added a link to this repository. Preserved the 16-page layout.
- **1.1 — September 28, 2026:** First repository edition. Replaced numbered model references and model-release comparisons with “Fable and Astra class models.” Cover labels now identify Claude Code and Codex. Removed release-specific timing language from the revised passages; clarified that agent nesting depends on tools and runtime. Added web-readable resources and two copyable excerpts alongside the PDF. Preserved the 16-page layout.
- **1.0 — 2026:** Original companion PDF.

## Keep going

Follow [Patrick on YouTube](https://www.youtube.com/@PatrickOakleyEllis) for future tutorials, or visit [patrickellis.io](https://patrickellis.io) for more of his work.

If this guide helps, a [star on the repository](https://github.com/OneRedOak/claude-code-workflows) makes it easy to find again.

[All guides](../README.md) · [Repository home](../../README.md)
