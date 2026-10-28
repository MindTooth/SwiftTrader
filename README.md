# SwiftTrader

Native macOS fleet commander and automation client for [SpaceTraders](https://spacetraders.io/), inspired by the tactical overview and industrial gameplay of EVE Online.

> **Status: planning / bootstrap.** No Xcode app, background service, or SpaceTraders integration is implemented yet. Do not interpret this repository as a playable game.

## Product

SwiftTrader combines a stylized 3D strategic fleet view with durable, unattended ship automation. The fleet engine must keep working when the tactical window closes, while the Mac is awake and the per-user background service is running.

**Stack under evaluation:** Swift 6, SwiftUI/AppKit, RealityKit, Swift Concurrency, SQLite, XPC, and a bundled launch agent managed with ServiceManagement. Architectural choices are documented in [docs/architecture.md](docs/architecture.md).

## Start here

- **Developers:** [docs/development.md](docs/development.md) for tooling, setup, workflow, and verification.
- **Coding agents:** [AGENTS.md](AGENTS.md) for scope, safety, and validation rules.
- **Product behavior:** [docs/product.md](docs/product.md).
- **System architecture:** [docs/architecture.md](docs/architecture.md).
- **Work sequence:** [docs/roadmap.md](docs/roadmap.md).
- **Design decisions:** [docs/adr/](docs/adr/).
- **Contributing:** [CONTRIBUTING.md](CONTRIBUTING.md).

## Current milestones

1. Bootstrap a buildable macOS Xcode project and testable Swift packages.
2. Implement a typed SpaceTraders client and fixture-driven tests.
3. Build a durable, single-writer fleet automation engine.
4. Add a native menu bar controller and supported background service lifecycle.
5. Add the tactical RealityKit view and configurable strategies.

Track individual work in GitHub Issues. Keep accepted architectural decisions in the repository; use short-lived feature plans in `docs/plans/`.

## Safety and boundaries

The SpaceTraders API is authoritative for credits, inventory, navigation, and action results. The renderer only visualizes state. Never store bearer tokens in source control or logs. The game is **not** EVE Online and does not replicate its assets, trademarks, or real-time combat.

## License

No license has been selected yet. Do not assume permission to redistribute this repository's code until a license is added.
