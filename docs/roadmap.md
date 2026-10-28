# Roadmap

All stages are planned; none are implemented.

## M0 — Buildable native foundation
Create SwiftUI macOS app, background engine executable target, testable Swift packages, Xcode schemes, fixtures, and macOS CI. **Done:** empty app builds/launches; package tests pass.

## M1 — API and read-only fleet
SpaceTraders authentication, Keychain, typed agent/ships/systems client, rate limiter, mock HTTP tests. **Done:** real fleet can be inspected without issuing game mutations.

## M2 — Durable engine and native background lifecycle
SQLite job state machine, single-writer semantics, scheduler, reconciliation, XPC, launch agent, menu bar. **Done:** restart and UI closure do not duplicate or lose scheduled work, subject to Mac wake/login.

## M3 — First safe automation
Single-ship extraction / haul workflow, explicit policy bounds, errors, audit history, deterministic fixture testing. **Done:** demonstrable end-to-end unattended workflow and restart recovery.

## M4 — Tactical 3D fleet command
RealityKit stylized system, ship/waypoint selection, navigation routes, context commands, UI state snapshots. **Done:** inspect automated fleet in the 3D window with no rendering when window is closed.

## M5 — Economics and expansion
Markets, contracts, route profitability and broader strategies after real API semantics are validated.

Track implementation as GitHub Issues. Plans belong under `docs/plans/` when needed; never treat roadmap descriptions as already-built capabilities.
