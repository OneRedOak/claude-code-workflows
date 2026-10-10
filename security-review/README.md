# Security Review Workflow

This directory contains templates and examples for implementing an automated security review system that provides comprehensive vulnerability scanning and security analysis on code changes. This workflow is inspired by and taken from Anthropic's [claude-code-security-review](https://github.com/anthropics/claude-code-security-review) GitHub repository, enabling teams to proactively identify and address security issues before they reach production.

## Concept

This workflow establishes a comprehensive methodology for automated security reviews in Claude Code, leveraging AI agents to detect vulnerabilities and enforce security best practices:

**Core Methodology:**
- **Automated Security Scanning**: Deploy AI-powered security reviewers that identify vulnerabilities, exposed secrets, and potential attack vectors
- **OWASP-Based Analysis**: Follow industry-standard security frameworks including OWASP Top 10 to ensure comprehensive coverage
- **Severity Classification**: Automatically categorize findings by severity level (Critical, High, Medium, Low) with clear remediation guidance
- **False Positive Management**: Intelligent filtering to reduce noise and focus on real security issues

**Implementation Features:**
- **Slash Commands**: Enable instant security reviews with `/security-review` that analyzes recent changes for security vulnerabilities
- **GitHub Actions Integration**: Automated security scanning on every PR, with inline comments highlighting specific security concerns
- **Secret Detection**: Identify exposed API keys, credentials, and sensitive information before they're committed
- **Dependency Analysis**: Review third-party dependencies for known vulnerabilities and security risks
- **Custom Security Policies**: Configure organization-specific security requirements and compliance standards

This approach ensures that security is built into the development process from the start, catching vulnerabilities early when they're easiest and least expensive to fix.

## Resources

### Templates & Examples
- [Security Review Slash Command](./security-review-slash-command.md) - Default security review command from Anthropic (source: [claude-code-security-review](https://github.com/anthropics/claude-code-security-review))
- [Security YAML](./security.yml) - GitHub Action configuration for automated security scanning
- [MiniMax Security YAML](./security-minimax.yml) - Security scanning configuration backed by MiniMax's Anthropic-compatible endpoint

### Video Tutorial
For a detailed walkthrough of this workflow, watch the [comprehensive tutorial on YouTube](https://www.youtube.com/watch?v=nItsfXwujjg).
