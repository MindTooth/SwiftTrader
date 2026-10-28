# Contributing

## Before you start
Read [README.md](README.md), [docs/development.md](docs/development.md), [docs/architecture.md](docs/architecture.md), and [AGENTS.md](AGENTS.md). This project is currently documentation-only; bootstrap the Xcode project before invoking build commands.

## Changes
1. Find or open a focused GitHub Issue with problem, scope, acceptance criteria, and test plan.
2. Create a branch such as `feat/issue-12-api-client`, `fix/issue-15-recovery`, or `docs/issue-7-setup`.
3. Make a plan in `docs/plans/` for work involving multiple modules, background lifecycle, or significant risk. Small fixes can plan in the PR.
4. Implement with focused tests, preserve module boundaries, and include errors/recovery behavior.
5. Open a PR describing motivation, implementation, actual validation, risks, and issue link.

## Definition of done
- Acceptance criteria satisfied; automated tests added where appropriate.
- Relevant `swift build`, `swift test`, `xcodebuild build` and Xcode tests executed where targets exist, or explicitly marked not run.
- No credentials or account-specific data; no live mutations in default tests.
- Documentation and ADRs updated for behavioral or architectural changes.
- PR reviewed and CI green when available.

## Review
Prefer small independent PRs. Avoid speculative refactors and mixing generated API files with unrelated changes. Record design disagreements in ADRs, not undocumented chat history.

## Task state
GitHub Issues: authoritative backlog; docs/roadmap.md: sequence; docs/plans/: scoped implementation approach; `.agents/checkpoint.md`: temporary local progress for one task only.
