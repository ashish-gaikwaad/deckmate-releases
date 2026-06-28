# Changelog

All notable changes to DeckMate will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial release: single Flutter project for macOS, Linux, Windows (host) and Android, iOS (remote)
- Multi-tray button grid with add / rename / delete tray support
- System actions: lock, sleep, screenshot, volume, media controls, brightness
- WebSocket communication over local WiFi (port 4321)
- Connected host info card on remote (hostname, platform, IP)
- Keep screen awake toggle on remote
- System tray with grey/green status icon (macOS, Linux, Windows)
- QR code on host status window for easy pairing
- Exponential backoff reconnect on remote (2 s → 30 s)
