# Claude Code Workflows
The best workflows and configurations I've developed heavily using Claude Code since the day of it's release. Workflows are based off applied learnings from our AI-native startup. 

Workflows are covered in detail with tutorials and demos on [Patrick Ellis' YouTube channel](https://www.youtube.com/@PatrickOakleyEllis).

## Workflows

### [Code Review Workflow](./code-review/)
An automated code review system inspired by Anthropic's own Claude Code development process, where AI agents handle the "blocking and tackling" of code review. This workflow implements dual-loop architecture with slash commands and GitHub Actions to automatically review PRs for syntax, completeness, style guide adherence, and bug detection. Free your team to focus on strategic thinking and architectural alignment while AI handles routine checks. [Watch the tutorial](https://www.youtube.com/watch?v=nItsfXwujjg).

### [Security Review Workflow](./security-review/)
An automated security review system that proactively identifies vulnerabilities, exposed secrets, and potential attack vectors in your codebase. Based on Anthropic's security-focused approach and OWASP Top 10 standards, this workflow provides severity-classified findings with clear remediation guidance. Includes slash commands for on-demand scanning and GitHub Actions for automated PR security checks. [Watch the tutorial](https://www.youtube.com/watch?v=nItsfXwujjg).

### [Design Review Workflow](./design-review/)
An automated design review system that provides comprehensive feedback on front-end code changes. This workflow uses Microsoft's open source [Playwright MCP](https://github.com/microsoft/playwright-mcp) browser automation and specialized Claude Code agents to ensure UI/UX consistency, accessibility compliance, and adherence to world-class design standards. Perfect for maintaining design quality across teams and catching visual issues before they reach production. [Watch the tutorial](https://www.youtube.com/watch?v=xOO8Wt_i72s).

### [Design System Architect Workflow](./design-system-architect/)
A comprehensive design system creation and management workflow that generates design tokens, component specifications, and style guides from brand assets. Creates the foundation standards that the Design Review Workflow validates against, enabling automated design consistency across projects. Features accessibility-first approach, multi-framework support, and seamless integration with design tools.

**Perfect Integration**: Use Design System Architect to create your design standards, then let Design Review Workflow validate all implementations against those standards for complete design system lifecycle management.

---

*More workflows coming soon...*
