# DeckMate — Testing Guide

## Prerequisites

- Flutter SDK installed and on PATH (`flutter doctor` passes)
- macOS: Xcode 15+ installed
- Android: physical device with USB debugging, or emulator running
- Both Mac and phone on the **same WiFi network**

---

## Step 1 — Run the Host (Mac)

```bash
cd /Users/ashish/Cooee/Web/deckmate
flutter run -d macos
```

**Expected:**
- A small circle icon appears in the menu bar (top-right)
- Clicking it opens a window with your local IP (e.g. `192.168.1.42:4321`) and a QR code
- Icon is grey — no remote connected yet

Note the IP address shown.

---

## Step 2 — Run the Remote (Android)

```bash
flutter run -d android
```

> **Emulator?** Use IP `10.0.2.2` instead of your actual Mac IP.

**Expected:**
- App opens showing 6 default buttons
- Status chip in top-right shows "Offline" (red) initially

---

## Step 3 — Connect

1. Tap **Settings** in the bottom nav
2. Enter the IP from Step 1 (e.g. `192.168.1.42`)
3. Port should be `4321` (default)
4. Tap **Save & Reconnect**

**Expected:**
- Settings screen shows "Connected to host" (green)
- Mac menu bar icon turns green
- Back on the Deck screen, status chip shows "Live" (green)

---

## Step 4 — Test Button Actions

| Action | Expected on Mac |
|---|---|
| Tap 🌐 Chrome | Google Chrome opens |
| Tap 💬 Slack | Slack opens |
| Tap 🐙 GitHub | Browser opens github.com |
| Tap 🖥️ Terminal | Terminal opens |

Each tap should also animate (brief scale-down) on the phone.

---

## Step 5 — Test Edit / Add / Delete

1. **Long-press** the Chrome button
2. Edit button sheet opens — change label to "Browser", emoji to "🔵"
3. Tap **Save Changes**
4. Button updates immediately in the grid
5. **Kill and reopen** the app — change should persist

**Add a button:**
1. Tap the **+** tile at the end of the grid
2. Set: icon `📧`, label `Mail`, type `URL`, value `https://mail.google.com`
3. Tap **Add Button**
4. New button appears — tap it → browser opens Gmail

**Delete a button:**
1. Long-press any button → edit sheet
2. Tap the trash icon (top-right of sheet)
3. Button is removed from grid

---

## Step 6 — Test Reconnection

1. Quit the Mac app (right-click tray icon → Quit)
2. Remote app status turns red within ~2s
3. Relaunch Mac app (`flutter run -d macos`)
4. Remote auto-reconnects within ~4s (exponential backoff)
5. Status turns green again without any manual action

---

## Step 7 — Test on Linux (Ubuntu)

```bash
# On Ubuntu machine
flutter run -d linux
```

Expected: same tray icon behaviour, `xdg-open` is used instead of `open -a`.

To test app opening on Linux, add a button with value `/usr/bin/firefox` (or any installed binary path) and action type `app`.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Mac app launches but no tray icon | Check macOS entitlements: `bash .deckmate_config/apply_patches.sh` |
| Remote can't connect | Confirm both devices on same WiFi; check Mac firewall allows port 4321 |
| Emulator can't connect | Use `10.0.2.2` as the host IP, not your Mac's LAN IP |
| App crashes on macOS | Run `flutter run -d macos --verbose` to see the error |
| Linux tray icon missing | Install `libayatana-appindicator3-dev`: `sudo apt install libayatana-appindicator3-dev` |
