# Code Review Workflow

This directory contains templates and examples for implementing an automated code review system that provides comprehensive feedback on code changes. This workflow, inspired by Anthropic's own Claude Code development process and their [claude-code-action](https://github.com/anthropics/claude-code-action) GitHub repository, enables teams to scale code review capacity while maintaining high quality standards through AI-assisted reviews.

## Concept

This workflow establishes a comprehensive methodology for automated code reviews in Claude Code, replacing manual line-by-line reviews with intelligent AI agents that handle pattern matching and consistency checks:

**Core Methodology:**
- **Automated Code Reviews**: Deploy AI reviewers that handle the "blocking and tackling" of code review - syntax, completeness, style guide adherence, and bug detection
- **Dual-Loop Architecture**: Leverage both inner loop (slash commands, subagents) for iterative development and outer loop (GitHub Actions) for automated PR validation
- **Standards-Based Evaluation**: Enforce consistent code quality through pattern matching, fast analysis, and adherence to your team's specific coding standards
- **Human-AI Collaboration**: Free human reviewers to focus on high-level strategic thinking, architectural alignment, and business logic while AI handles routine checks

**Implementation Features:**
- **Claude Code Subagents**: Deploy specialized code review agents that preserve context and provide detailed analysis without consuming main thread tokens
- **Slash Commands**: Enable instant code reviews with `/review` that automatically analyzes recent commits or specified PRs
- **GitHub Actions Integration**: Fully automated reviewers that run on every PR, providing consistent feedback before human review
- **Customizable Review Criteria**: Tailor review standards to your organization's specific needs, architectural patterns, and coding conventions
- **Learning Opportunities**: Teams learn from AI-generated reviews, improving their understanding of best practices and common pitfalls

This approach, battle-tested by Anthropic's own engineering team building Claude Code with Claude Code, enables teams to handle the increased volume of AI-generated code while maintaining rigorous quality standards.

## Resources

### Templates & Examples
- [Claude Code Review YAML](./claude-code-review.yml) - Standard GitHub Action configuration for automated code reviews
- [Custom Code Review YAML](./claude-code-review-custom.yml) - Extended configuration with custom review criteria
- [MiniMax Code Review YAML](./claude-code-review-minimax.yml) - Standard review configuration backed by MiniMax's Anthropic-compatible endpoint
- [Custom MiniMax Code Review YAML](./claude-code-review-custom-minimax.yml) - Extended review configuration backed by MiniMax's Anthropic-compatible endpoint
- [Pragmatic Code Review Slash Command](./pragmatic-code-review-slash-command.md) - Custom slash command for on-demand pragmatic code reviews
- [Pragmatic Code Review Subagent](./pragmatic-code-review-subagent.md) - Subagent configuration for comprehensive code analysis

### Video Tutorial
For a detailed walkthrough of this workflow, watch the [comprehensive tutorial on YouTube](https://www.youtube.com/watch?v=nItsfXwujjg).
