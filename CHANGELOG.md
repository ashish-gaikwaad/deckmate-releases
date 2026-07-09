# Changelog

All notable changes to DeckMate will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.1] — 2026-07-09

### Added
- macOS app icons are now transmitted over WebSocket and displayed on mobile button tiles
- QR code scanner on the mobile settings screen for instant pairing
- Landscape orientation fully supported on Android/iOS — navigation rail replaces bottom bar, grid expands to 4 columns, header and tray bar shrink

### Fixed
- macOS: App now appears in Cmd+Tab app switcher
- macOS: Clicking the menu bar icon now opens the app window (was a no-op previously)
- macOS: Closing the window keeps the app alive in the menu bar instead of quitting
- Android: Camera permission is explicitly requested before opening the QR scanner; permanently denied case shows a dialog linking to app settings
- macOS: SetApp and JetBrains Toolbox apps now appear in the app picker

### Changed
- App bundle ID updated to `com.ags.deckmate`
- App display name corrected to `DeckMate`

## [1.0.0] — 2026-06-29

### Added
- Initial release: single Flutter codebase for macOS, Linux, Windows (host) and Android, iOS (remote)
- Multi-tray button grid with add / rename / delete tray support; trays sync bidirectionally between host and remote
- Button types: App (opens application), URL (opens browser), System (built-in commands)
- System actions: lock screen, sleep, screenshot, volume up/down/mute, play/pause, next/prev track, brightness up/down
- Real macOS app icons displayed on desktop button tiles
- WebSocket server on host (port 4321) with bidirectional tray sync
- Screen always awake on mobile while DeckMate is open
- System tray with grey/green status icon reflecting connection state (macOS, Linux, Windows)
- QR code displayed on host status window for easy pairing
- Auto-reconnect on remote with exponential backoff (2 s → 30 s)
- Connected host info card showing hostname, platform, and IP
- Modern dark UI with per-type accent colours and press animations on mobile
