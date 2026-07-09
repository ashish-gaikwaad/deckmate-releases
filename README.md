# DeckMate

**Turn your phone into a programmable button pad for your Mac, Windows PC, or Linux desktop.**

DeckMate is a free alternative to a physical Stream Deck. Install the app on your phone, install the companion on your computer, connect to the same Wi-Fi — and you have a fully customisable remote control on your phone screen.

> No cloud. No accounts. Everything stays on your local network.

**GitHub:** [ashish-gaikwaad/deckmate-releases](https://github.com/ashish-gaikwaad/deckmate-releases) · [Releases](https://github.com/ashish-gaikwaad/deckmate-releases/releases) · [Changelog](./CHANGELOG.md)

---

## What you can do

- Launch any app on your computer with one tap
- Open any website instantly
- Control system functions — volume, media playback, screen lock, sleep, screenshot, and brightness
- Organise buttons into multiple **Trays** (pages) — one for work, one for music, one for system controls
- Add, edit, or remove buttons any time
- Keep your phone screen awake while DeckMate is open

---

## Compatibility

### Phone (Remote)

| Platform | Minimum version |
|----------|----------------|
| Android | Android 5.0 (API 21) |
| iPhone / iPad | iOS 13 |

### Computer (Host)

| Platform | Minimum version |
|----------|----------------|
| macOS | macOS 10.15 Catalina |
| Windows | Windows 10 (64-bit) |
| Linux / Ubuntu | Ubuntu 20.04 or any distro with GTK3 |

> Both devices must be on the **same local Wi-Fi network**.

---

## Download

Go to the [**Releases**](https://github.com/ashish-gaikwaad/deckmate-releases/releases) page and grab the build for your platform:

| Platform | File |
|----------|------|
| Android | `DeckMate-x.x.x-android.apk` |
| macOS | `DeckMate-x.x.x-macos.dmg` |

> **iOS:** Sideload via AltStore, or install via TestFlight if you have an invite link.

---

## Setup

### Step 1 — Install on your computer

**macOS**
1. Open `DeckMate-macos.dmg`
2. Drag **DeckMate** to your Applications folder
3. Launch it — a small icon appears in the **menu bar** (top-right of your screen)
4. Click the icon → the status window opens showing your local IP address and a QR code

**Windows**
1. Run `DeckMate-windows-setup.exe` and follow the installer
2. Launch DeckMate — a small icon appears in the **system tray** (bottom-right)
3. Click the icon → you'll see your local IP address and a QR code

**Linux**
1. Make the file executable: right-click → Properties → Allow executing as program
   (or run: `chmod +x DeckMate-linux.AppImage`)
2. Launch it — a **tray icon** appears in your notification area
3. Click the icon → you'll see your local IP address and a QR code

---

### Step 2 — Install on your phone

**Android**
1. Transfer `DeckMate-android.apk` to your phone (download directly or via cable)
2. Tap the file to install — if prompted, allow installation from unknown sources
3. Open **DeckMate**

**iPhone / iPad**
- Follow the sideload instructions included with the release note, or use the TestFlight link if you received an invite

---

### Step 3 — Connect phone to computer

1. Open DeckMate on your **phone**
2. Tap the **Settings** tab (bottom-right)
3. Tap **Scan QR Code from Mac** and point your camera at the QR code on your computer screen
   — or enter the IP address manually
4. Tap **Save & Reconnect**
5. The status indicator turns **green** — you're connected

---

## How to use

### Tapping buttons

Tap any button on the grid — the action fires on your computer instantly.

---

### Adding a button

On your **computer**, open the DeckMate status window and switch to the **Trays** tab. Add buttons there — they sync to your phone automatically.

---

### Trays (button pages)

The row of chips at the top of the mobile grid is your **Tray bar** — each tray is an independent page of buttons.

| Action | How |
|--------|-----|
| Switch tray | Tap a tray chip |
| Add a new tray | Use the Trays tab on your computer |

---

### System commands

| Button | What happens on your computer |
|--------|------------------------------|
| 🔒 Lock Screen | Locks the screen immediately |
| 😴 Sleep | Puts the computer to sleep |
| 📸 Screenshot | Takes a screenshot |
| 🔊 Volume Up | Increases volume |
| 🔉 Volume Down | Decreases volume |
| 🔇 Mute / Unmute | Toggles mute |
| ⏯️ Play / Pause | Plays or pauses the current media |
| ⏭️ Next Track | Skips to the next track |
| ⏮️ Previous Track | Goes back to the previous track |
| ☀️ Brightness Up | Increases screen brightness |
| 🌑 Brightness Down | Decreases screen brightness |

---

## Troubleshooting

**Phone shows "Not connected"**
- Confirm both devices are on the same Wi-Fi network
- Double-check the IP address matches what the tray icon shows
- Check that port `4321` is not blocked by a firewall

**Button tap does nothing**
- Check the status is green in the Settings tab
- **macOS:** System Settings → Privacy & Security → Accessibility → allow DeckMate

**DeckMate doesn't appear in the macOS Dock**
- This is intentional — DeckMate is a menu bar app. Find it by the small icon in the top-right menu bar. It also appears in Cmd+Tab.

**macOS says the app is from an unidentified developer**
- Right-click (or Control-click) the app → Open → Open anyway. You only need to do this once.

**Android camera doesn't open for QR scan**
- Go to Settings → tap **Scan QR Code from Mac** → grant Camera permission when prompted
- If previously denied: Settings → Apps → DeckMate → Permissions → Camera → Allow

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for the full version history.

---

## Feedback & bug reports

Open an issue on [this repository](https://github.com/ashish-gaikwaad/deckmate-releases/issues) — feature requests and bug reports are both welcome.
