# ADR 0001 — Native Swift first

- Status: Accepted as initial project direction
- Date: 2026-10-28

## Decision
Build SwiftTrader in Swift with SwiftUI/AppKit for macOS UI and RealityKit for stylized strategic 3D. Use Swift Concurrency for domain orchestration. Avoid Godot, Electron, and a Go service in the first implementation.

## Rationale
Native menu bar, window behavior, ServiceManagement, Keychain, debugging and distribution matter more than cross-platform portability.

## Consequences
Requires macOS/Xcode for full integration validation. Keep core logic platform-light and the renderer replaceable. Revisit only when there is a concrete technical bottleneck.
