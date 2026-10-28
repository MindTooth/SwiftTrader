# Agent instructions

This file is the entry point for Codex and other coding agents. Follow [CONTRIBUTING.md](CONTRIBUTING.md) and [docs/development.md](docs/development.md) for human/agent shared workflow.

## Read before editing
1. Read README.md, docs/product.md, docs/architecture.md and docs/roadmap.md.
2. Inspect the actual repository and issue; do not assume planned files or features already exist.
3. For a cross-module or high-risk change, add a concise plan under docs/plans/ before implementation.

## Non-negotiable boundaries
- Native macOS, Swift-first. Do not introduce Godot, Electron, Go services or other runtimes without an approved ADR.
- The headless engine alone submits **mutating** SpaceTraders API commands. UI and menu bar send typed intents.
- The SpaceTraders server is authoritative for ship actions, cargo, credits, navigation and cooldowns.
- Treat any interrupted or timed-out mutation as **uncertain**; reconcile remote state and do not blindly retry non-idempotent requests.
- Persist command intent before dispatch; design restart-safe jobs and rate-limited requests.
- Secrets in Keychain, never Git, SQLite plaintext, test fixtures or logs. Use mocks for default tests.
- The engine must survive closing the UI; do not prevent macOS from sleeping by default.
- No root privileges, public control ports, unapproved network access, or destructive live-account testing.
- Use original art and terminology; do not copy EVE Online assets.

## How to work
- One GitHub issue per focused branch/worktree; reference the issue in the PR.
- Keep implementation plans per-feature in docs/plans/; ADRs record durable decisions.
- Optional .agents/checkpoint.md is a **gitignored, single-task scratchpad**; delete it when that task finishes.
- Prefer test-first changes to domain, persistence, command handling, and API error paths.
- Validate with swift build/test for Swift packages and xcodebuild for the macOS app **when those targets exist**. Never report nonexistent checks as passing.
- External Codex can connect to an opened Xcode via `codex mcp add xcode -- xcrun mcpbridge` when Xcode supports and authorizes it. CLI tools are valid fallbacks.
- Never auto-merge, push credentials, or make real fleet transactions without explicit authorization.
- Finish with: summary, changed paths, checks actually executed (with results), blockers, and follow-up issues.
