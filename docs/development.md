# Developer setup

## Current state
The repository is an initial **documentation-only** project. No `.xcodeproj`, `Package.swift`, scheme, Swift source files, or CI job exists yet. Bootstrap is the first implementation task.

## Requirements
- Apple Silicon Mac recommended.
- Recent Xcode with macOS SDK and Command Line Tools installed.
- Git and SSH access to GitHub.
- Optional: standalone Codex app or CLI with Xcode's official MCP bridge.

Verify your local environment:
```sh
xcode-select -p
xcodebuild -version
swift --version
git --version
```

Clone:
```sh
git clone git@github.com:MindTooth/SwiftTrader.git
cd SwiftTrader
```

## Codex / Xcode
Use external Codex as the primary agent and Xcode as IDE, debugger, previews and build environment. In Xcode, enable external MCP agent access in its settings if supported. Add bridge to Codex:
```sh
codex mcp add xcode -- xcrun mcpbridge
codex mcp list
```
Keep Xcode open on the project during bridge use. MCP authorization and feature availability vary by installed Xcode version; `xcodebuild` remains the reproducible fallback. Do not rely on the Codex version bundled inside Xcode.

## Validation
After the bootstrap task creates targets, document real scheme names here and run:
```sh
swift build
swift test
xcodebuild -list -project SwiftTrader.xcodeproj
```
Run `xcodebuild build` and tests using **actual**, discovered scheme and destination values, not guessed ones. Today these commands (except tool version checks) are **not runnable against this repo**.

## Safe development
- Prefer fake API responses and recorded sanitized fixtures; never use a live account in CI.
- Do not store bearer tokens in source, environment files committed to Git, logs, or screenshots.
- Live API actions require explicit local opt-in, dry-run preview where feasible, and spend/fuel constraints.
- Follow [CONTRIBUTING.md](../CONTRIBUTING.md) for issue, PR, and verification standards.
