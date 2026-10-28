# Product specification

## Vision
A native macOS, EVE-inspired **strategic fleet commander** for the SpaceTraders API, not a realtime space-flight simulator.

## Primary experience
- Stylized 3D strategic system view: orbit/zoom/pan, ships and waypoints, projected routes, selection and inspector.
- Fleet management: assignments, cargo, current navigation, cooldown, contracts and industry.
- Automation-first: mine, deliver, trade and explore through explicit safe, auditable, configurable strategies.
- Native SwiftUI fleet panels and menu bar status with notifications.

## Background behavior
Closing a tactical window must not halt a running strategy. Per-user background engine runs independently when enabled. Explicit pause stops issuing further commands; in-flight API operations cannot necessarily be canceled. Sleep interrupts operation until wake/reconciliation. Login-start is opt-in and subject to OS approval. Quit/stop engine semantics must be obvious.

## Initial gameplay slice
Launch app → connect an agent → view ships and system → assign a single mining workflow → close window → verify background progress → reopen and inspect history. For live trading, use an explicit confirmation and configured transaction bounds.

## Out of scope for v0.1
Real-time combat, independent game server, continuous free-flight physics, EVE assets, always-on cloud operation, autonomous unrestricted purchases, complex multi-account operation.

## Success criteria
Correctness and safe restart reconciliation take precedence over frame rate or cinematic polish. Real account actions must be opt-in, bounded and auditable.
