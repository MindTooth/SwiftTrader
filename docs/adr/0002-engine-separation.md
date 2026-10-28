# ADR 0002 — Independent per-user engine

- Status: Accepted as initial project direction
- Date: 2026-10-28

## Decision
Run automation in a separate, unprivileged Swift process managed by a per-user launch agent, with typed local IPC. UI and 3D renderer may exit without stopping jobs.

## Rationale
A menu bar or 3D window should not determine the lifetime or correctness of persistent fleet automation.

## Consequences
Invest in IPC versioning, durable persistence, startup reconciliation, and transparent user lifecycle controls. Background work does not continue while Mac sleeps or is shut down. Start at login requires supported OS registration and user approval.
