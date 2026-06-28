# DeckMate

**Turn your phone into a programmable button pad for your Mac, Windows PC, or Linux desktop.**

DeckMate is a free alternative to a physical Stream Deck. Install the app on your phone, install the companion on your computer, connect to the same Wi-Fi — and you have a fully customisable remote control on your phone screen.

> No cloud. No accounts. Everything stays on your local network.

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

Go to the [**Releases**](../../releases) page and grab the build for your platform:

| Platform | File |
|----------|------|
| Android | `deckmate-android.apk` |
| macOS | `DeckMate-macos.dmg` |
| Windows | `DeckMate-windows-setup.exe` |
| Linux | `DeckMate-linux.AppImage` |

> **iOS:** Sideload via AltStore, or install via TestFlight if you have an invite link.

---

## Setup

### Step 1 — Install on your computer

**macOS**
1. Open `DeckMate-macos.dmg`
2. Drag **DeckMate** to your Applications folder
3. Launch it — a small icon appears in the **menu bar** (top-right of your screen)
4. Click the icon → you'll see your local IP address and a QR code

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
1. Transfer `deckmate-android.apk` to your phone (download directly or via cable)
2. Tap the file to install — if prompted, allow installation from unknown sources
3. Open **DeckMate**

**iPhone / iPad**
- Follow the sideload instructions included with the release note, or use the TestFlight link if you received an invite

---

### Step 3 — Connect phone to computer

1. Open DeckMate on your **phone**
2. Tap the **Settings** tab (bottom-right)
3. Enter the **IP address** shown in the computer's tray icon popup
   — or tap **Scan QR** to scan the QR code from the computer screen
4. Tap **Save & Reconnect**
5. The status indicator turns **green** — you're connected

---

## How to use

### Tapping buttons

Tap any button on the grid — the action fires on your computer instantly.

---

### Adding a button

Tap the **＋** tile at the end of the grid, then choose an action type:

| Type | What it does | Example |
|------|-------------|---------|
| **App** | Opens an application | `/Applications/Slack.app` · `C:\Program Files\...` |
| **URL** | Opens a link in the browser | `https://github.com` |
| **⚙️ System** | Triggers a built-in system action | Pick from the list below |

Give the button a label and an emoji icon, then tap **Add Button**.

---

### Editing or deleting a button

**Long-press** any button → tap **Edit**. Change the label, emoji, or action. Tap the 🗑️ icon to delete it.

---

### Trays (button pages)

The row of chips at the top is your **Tray bar** — each tray is an independent page of buttons.

| Action | How |
|--------|-----|
| Switch tray | Tap a tray chip |
| Rename or delete tray | Long-press a tray chip |
| Add a new tray | Tap **＋** in the tray bar |

The app ships with two trays:
- **Main 🏠** — six app shortcuts (Chrome, Slack, Spotify, Finder, Terminal, GitHub)
- **System ⚙️** — all 11 system commands, ready to use

---

### System commands

| Button | What happens on your computer |
|--------|------------------------------|
| 🔒 Lock Screen | Locks the screen immediately |
| 😴 Sleep | Puts the computer to sleep |
| 📸 Screenshot | Takes a screenshot |
| 🔊 Volume Up | Increases volume by 10% |
| 🔉 Volume Down | Decreases volume by 10% |
| 🔇 Mute / Unmute | Toggles mute |
| ⏯️ Play / Pause | Plays or pauses the current media |
| ⏭️ Next Track | Skips to the next track |
| ⏮️ Previous Track | Goes back to the previous track |
| ☀️ Brightness Up | Increases screen brightness |
| 🌑 Brightness Down | Decreases screen brightness |

> Brightness control works on MacBooks and most laptops. Desktop monitors may not respond depending on driver support.

---

## Settings reference

| Setting | Description |
|---------|-------------|
| **Host IP Address** | Your computer's local network IP (shown in the tray icon popup) |
| **Port** | Default is `4321`. Change only if you have a port conflict |
| **Keep Screen Awake** | Prevents your phone screen from dimming while DeckMate is open |

---

## Troubleshooting

**Phone shows "Not connected"**
- Confirm both devices are on the same Wi-Fi network (not one on Wi-Fi and one on Ethernet with isolation)
- Double-check the IP address matches what the tray icon shows
- Check that port `4321` is not blocked by a firewall — temporarily disable it to test, then add an allow rule
- **macOS:** go to System Settings → Privacy & Security → Local Network and allow DeckMate

**Button tap does nothing / system actions don't work**
- Check the status is green in the Settings tab
- **macOS:** go to System Settings → Privacy & Security → Accessibility and allow DeckMate (required for media keys, lock screen, and screenshot shortcuts)

**DeckMate doesn't appear in the macOS Dock**
- This is intentional — DeckMate is a menu bar app. Find it by the small icon in the top-right menu bar.

**Buttons disappeared after reinstalling**
- Button layouts are stored on your **phone**. Reinstalling the phone app resets them to defaults. Reinstalling the computer app has no effect on your buttons.

**Android can't connect from an emulator**
- Use `10.0.2.2` as the host IP instead of your machine's local IP.

**macOS says the app is from an unidentified developer**
- Right-click (or Control-click) the app → Open → Open anyway. You only need to do this once.

---

## Default buttons

| | Label | Action |
|-|-------|--------|
| 🌐 | Chrome | Opens Google Chrome |
| 💬 | Slack | Opens Slack |
| 🎵 | Spotify | Opens Spotify |
| 📁 | Finder | Opens Finder |
| 🖥️ | Terminal | Opens Terminal |
| 🐙 | GitHub | Opens github.com |

All default buttons can be edited or deleted freely.

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for the full version history.

---

## Feedback & bug reports

Open an issue on this repository — feature requests and bug reports are both welcome.
