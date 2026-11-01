# Secure QA Agent MCP Server (TypeScript)

A production-grade Model Context Protocol (MCP) server built with TypeScript to connect AI Agents (Cursor Composer, Claude Code) securely to Jira, GitHub, and Sandbox Testing environments.

## 🛡️ Core Architecture & Guardrails
This project treats the AI Agent as an untrusted operator. System security policies are hardcoded at the runtime level:
- **Can Do:** Safe, read-only analytical queries (fetching GitHub PR diffs, looking up ticket criteria) are fully automated. Data payloads are structured to reduce token overhead.
- **Can't Do:** Structural mutations (updating Jira workflows, merging code) are **intercepted by default** using a Human-in-the-Loop (HITL) gate unless an encryption token is provided.
- **Audit Logging:** Outputs raw, standardized JSON tracking metrics to `stderr`, capturing timestamps, arguments, and security compliance passes for out-of-band monitoring.

