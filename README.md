# Claude Code Workflows
Practical workflows, configurations, and companion guides from my journey becoming an AI-native founder, for founders and software engineers building faster and smarter with AI.

Workflows are covered in detail with tutorials and demos on [Patrick Ellis' YouTube channel](https://www.youtube.com/@PatrickOakleyEllis).

## Start here

| If you want to… | Start with… |
| --- | --- |
| Build the context, tools, workflows, and verification around your agents | [The Orchestration Layer Playbook](./guides/orchestration-layer/) |
| Browse downloadable companion guides | [Guide library](./guides/) |
| Automate PR review | [Code review](./code-review/) |
| Review security risks | [Security review](./security-review/) |
| Review interfaces in the browser | [Design review](./design-review/) |

## Featured guide: The Orchestration Layer Playbook

A free, 16-page companion guide to building the four-pillar system around Claude Code and Codex: **context, tools, workflows, and verification**. Includes practical checklists, a review workflow, and a 30-day rollout plan.

**[Download the free PDF](https://raw.githubusercontent.com/OneRedOak/claude-code-workflows/main/guides/orchestration-layer/orchestration-layer-playbook.pdf)** · [Read the guide overview](./guides/orchestration-layer/) · [Browse tools and resources](./guides/orchestration-layer/resources.md)

Optional: [Join my newsletter](https://bhi-patrickellis.beehiiv.com/) for practical workflows and hard-won lessons as I build with Claude Code, Codex, Cursor, Gemini, ChatGPT, n8n, and image and video tools. The guide is free; no signup is required.

## Workflows

### [Code Review Workflow](./code-review/)
An automated code review system inspired by Anthropic's own Claude Code development process, where AI agents handle the "blocking and tackling" of code review. This workflow implements dual-loop architecture with slash commands and GitHub Actions to automatically review PRs for syntax, completeness, style guide adherence, and bug detection. Free your team to focus on strategic thinking and architectural alignment while AI handles routine checks. [Watch the tutorial](https://www.youtube.com/watch?v=nItsfXwujjg).

### [Security Review Workflow](./security-review/)
An automated security review system that proactively identifies vulnerabilities, exposed secrets, and potential attack vectors in your codebase. Based on Anthropic's security-focused approach and OWASP Top 10 standards, this workflow provides severity-classified findings with clear remediation guidance. Includes slash commands for on-demand scanning and GitHub Actions for automated PR security checks. [Watch the tutorial](https://www.youtube.com/watch?v=nItsfXwujjg).

### [Design Review Workflow](./design-review/)
An automated design review system that provides comprehensive feedback on front-end code changes. This workflow uses Microsoft's open source [Playwright MCP](https://github.com/microsoft/playwright-mcp) browser automation and specialized Claude Code agents to ensure UI/UX consistency, accessibility compliance, and adherence to world-class design standards. Perfect for maintaining design quality across teams and catching visual issues before they reach production. [Watch the tutorial](https://www.youtube.com/watch?v=xOO8Wt_i72s).

---

If these workflows help, consider starring this repository so you can find it again.
