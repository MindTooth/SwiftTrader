# Architecture (proposed)

**Status:** Target architecture, not yet implemented.

```text
SwiftUI/AppKit app + menu bar  -- typed local IPC -->  Swift FleetEngine LaunchAgent
    | RealityKit tactical renderer                   | scheduler / strategies
    | read-only snapshots and commands              | serialized command pipeline
                                                   +-- SQLite durable jobs/events
                                                   +-- Keychain credentials
                                                   +-- SpaceTraders v2 REST API
```

## Modules (planned)
- `FleetDomain`: ship, waypoint, task and command domain models without UI dependencies.
- `SpaceTradersAPI`: typed HTTP transport, authentication, errors and shared rate limiting.
- `FleetAutomation`: strategies, state machine, scheduling, retry/reconciliation rules.
- `FleetPersistence`: SQLite transactions, migrations, durable jobs and history.
- `FleetIPC`: versioned XPC contracts, authentication and state streaming.
- `FleetCommander`: SwiftUI/AppKit UI and RealityKit renderer.
- `FleetEngine`: headless per-user background process owning commands and database writes.

## Invariants
1. One command owner and one database writer: FleetEngine. UI cannot directly submit mutating SpaceTraders calls.
2. API response and subsequent reconciliation determine truth, not animations.
3. Persist before dispatch; model `queued → submitting → confirmed/uncertain → reconciled`, with failure/blocked states.
4. A lost response to a non-idempotent POST must not trigger an automatic replay.
5. Respect server rate limits (including shared IP/account limits); use server-driven cooldown and arrival scheduling.
6. Tokens in macOS Keychain; restrict IPC to local authorized client. Keep screenshots, test fixtures, and logs scrubbed.
7. After restart/wake, refresh account and ship state, detect server resets, reconcile uncertain actions, and resume only safe jobs.
8. Rendering never runs when UI is closed. launchd manages the per-user engine; no privileged daemon.

## Lifecycle
A signed app registers a bundled launch agent through ServiceManagement with user consent. Closing the window and pausing strategies are distinct actions. A stopped or sleeping Mac does not run fleet commands; resume after login/wake is conditional on the configured policy.

## Technology decisions to validate
- Swift 6, SwiftUI/AppKit, RealityKit, actors, SQLite (library selection open), XPC, ServiceManagement.
- macOS deployment target and Xcode/SDK compatibility should be pinned when bootstrap creates a buildable application.
- Maintain a fixture-backed fake API for deterministic tests before live integration.

See [ADR 0001](adr/0001-native-swift.md) and [ADR 0002](adr/0002-engine-separation.md).
