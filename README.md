# DeckMate

A cross-platform Stream Deck replacement built with a single Flutter project.

- **On Android / iOS** → shows a configurable button grid (the remote)
- **On macOS / Linux / Ubuntu** → runs a WebSocket server in the system tray (the host)

Same codebase, platform-detected at launch.

---

## How it works

```
┌──────────────────────┐    WebSocket (local WiFi)    ┌──────────────────────────┐
│  DeckMate            │ ───────────────────────────▶ │  DeckMate                │
│  Android / iOS       │                              │  macOS / Linux           │
│                      │  { actionType: "app",        │                          │
│  [🌐 Chrome]         │    value: "/Applications/…"} │  open -a "Chrome"        │
│  [💬 Slack  ]        │                              │                          │
│  [🎵 Spotify]        │ ◀─────────────────────────── │  Tray icon: ● connected  │
│                      │  { success: true }           │                          │
└──────────────────────┘                              └──────────────────────────┘
```

---

## Platforms

| Platform | Role | Status |
|---|---|---|
| Android (API 21+) | Remote (button pad) | ✓ |
| iOS (13+) | Remote (button pad) | ✓ |
| macOS (10.15+) | Host (tray server) | ✓ |
| Linux / Ubuntu | Host (tray server) | ✓ |
| Windows 10/11 | Host (tray server) | ✓ |

---

## Quick Start

### Prerequisites

- Flutter SDK ≥ 3.22 — `brew install --cask flutter` or [flutter.dev](https://flutter.dev/docs/get-started/install)
- macOS builds: Xcode 15+
- Linux builds: `sudo apt install clang cmake ninja-build libgtk-3-dev libayatana-appindicator3-dev`
- Windows builds: Visual Studio 2022 with "Desktop development with C++" workload
- Android: USB debugging enabled on device

### First-time setup

**macOS / Linux:**
```bash
cd /Users/ashish/Cooee/Web/deckmate
flutter create --platforms=macos,linux,windows,android,ios .
bash setup.sh
```

**Windows:**
```bat
cd path\to\deckmate
flutter create --platforms=windows,android,ios .
setup.bat
```

### Run

```bash
# Host (macOS tray app)
flutter run -d macos

# Host (Linux)
flutter run -d linux

# Host (Windows)
flutter run -d windows

# Remote (Android)
flutter run -d android

# Remote (iOS)
flutter run -d ios
```

### Build release

```bash
flutter build macos --release
flutter build linux --release
flutter build windows --release
flutter build apk --release
flutter build ios --release   # then archive in Xcode
```

### Releasing a new version

DeckMate uses [`cider`](https://pub.dev/packages/cider) (the Dart equivalent of `release-it`).

**Workflow:**

1. Add your changes under `## [Unreleased]` in `CHANGELOG.md`
2. Bump the version — choose one:
   ```bash
   dart run cider bump patch    # 1.0.0 → 1.0.1  (bug fix)
   dart run cider bump minor    # 1.0.0 → 1.1.0  (new feature)
   dart run cider bump major    # 1.0.0 → 2.0.0  (breaking change)
   ```
   This updates `pubspec.yaml` and moves `[Unreleased]` entries into a dated release section in `CHANGELOG.md`.
3. Commit and tag:
   ```bash
   git add pubspec.yaml CHANGELOG.md
   git commit -m "chore: Release $(dart run cider version)"
   git tag v$(dart run cider version)
   git push && git push --tags
   ```

---

## Default Buttons

| Emoji | Label | Action |
|---|---|---|
| 🌐 | Chrome | Opens Google Chrome |
| 💬 | Slack | Opens Slack |
| 🎵 | Spotify | Opens Spotify |
| 📁 | Finder | Opens Finder |
| 🖥️ | Terminal | Opens Terminal |
| 🐙 | GitHub | Opens github.com |

Long-press any button to edit it. Tap **+** to add a new one.

---

## Project Structure

```
lib/
├── main.dart                        # Platform detection → HostApp or RemoteApp
├── shared/
│   ├── models/deck_button.dart      # Button data model + default buttons
│   └── protocol/protocol.dart       # Shared constants (port, message types)
├── host/
│   ├── host_app.dart                # MaterialApp for desktop
│   ├── server/websocket_server.dart # shelf WebSocket server on port 4321
│   ├── executor/action_executor.dart# open -a / xdg-open
│   ├── tray/tray_controller.dart    # System tray icon (grey/green)
│   └── ui/status_window.dart        # IP address + QR code popup
└── remote/
    ├── remote_app.dart              # MaterialApp for mobile
    ├── network/websocket_client.dart# WS client + exponential backoff
    ├── data/button_repository.dart  # SharedPreferences persistence
    └── ui/
        ├── grid_screen.dart         # 3-col animated button grid
        ├── edit_button_sheet.dart   # Add / edit / delete buttons
        └── settings_screen.dart     # IP input + connection status
```

---

## Configuration

| Setting | Location | Default |
|---|---|---|
| Server port | `lib/shared/protocol/protocol.dart` → `kServerPort` | `4321` |
| Default buttons | `lib/shared/models/deck_button.dart` → `defaultButtons` | 6 preset buttons |

---

## Testing

See the [Testing Guide](./TESTING.md) for a full step-by-step walkthrough.

Quick matrix:

| Scenario | Expected |
|---|---|
| `flutter run -d macos` | Tray icon appears, status window shows IP + QR |
| Enter IP in remote → Save | Both sides show green |
| Tap app button | App opens on desktop |
| Tap URL button | Browser opens URL |
| Long press → edit → save | Change persists after restart |
| Kill host → relaunch | Remote auto-reconnects |
