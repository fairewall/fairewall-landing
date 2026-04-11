# fAIrewall Installation Guide

> **Version:** 1.0.0  
> **Last updated:** April 2026

fAIrewall is a local privacy firewall that intercepts and sanitizes PII from your AI prompts before they reach cloud providers. It consists of two components:

- **Desktop App** — Runs locally on your machine, performs all PII detection and masking
- **Chrome Extension** — Intercepts prompts from AI provider websites and routes them through the desktop app

Both components must be installed and running for full protection.

---

## Quick Overview

| Step | What | Time |
|------|------|------|
| 1 | Install the desktop app | 2 min |
| 2 | Install the Chrome extension | 1 min |
| 3 | Verify everything works | 1 min |

---

## 1. Desktop App — macOS

### Requirements

- macOS 12 (Monterey) or later
- Apple Silicon (M1/M2/M3/M4) or Intel

### Step-by-step

1. **Download** the latest `.dmg` file from [fairewall.ai/download](https://fairewall.ai/download).

2. **Open** the downloaded `.dmg` file. A Finder window will appear with the fAIrewall icon and an Applications folder shortcut.

3. **Drag** the fAIrewall icon into the Applications folder.

4. **Launch** fAIrewall from your Applications folder (or Spotlight: press `Cmd + Space`, type "fAIrewall", press Enter).

5. **Gatekeeper prompt:** On first launch, macOS may show a dialog saying the app was downloaded from the internet. Click **Open** to proceed. The app is notarized by Apple and safe to run.

6. **Verify the tray icon:** After launch, look for the fAIrewall shield icon in your macOS menu bar (top-right area). This confirms the app is running.

7. **Keep it running:** fAIrewall runs in the background. Closing the window minimizes it to the menu bar — it does not quit. To fully quit, right-click the tray icon and select **Quit fAIrewall**.

### Auto-start at login (optional)

To have fAIrewall start automatically when you log in:

1. Open the fAIrewall desktop app
2. Go to **Settings** (via the hamburger menu)
3. Enable **Start at login**

---

## 2. Desktop App — Windows

### Requirements

- Windows 10 (version 1809) or later
- 64-bit (x86_64)

### Step-by-step

1. **Download** the latest installer (`.exe`) from [fairewall.ai/download](https://fairewall.ai/download).

2. **Run** the installer. If Windows SmartScreen shows a warning ("Windows protected your PC"), click **More info**, then click **Run anyway**. This happens because the installer does not yet have an EV code signing certificate.

3. **Follow** the installation wizard. The default installation path is fine for most users.

4. **Launch** fAIrewall from the Start Menu or Desktop shortcut.

5. **Verify the tray icon:** After launch, look for the fAIrewall shield icon in the Windows system tray (bottom-right area, near the clock). You may need to click the `^` arrow to see it.

6. **Keep it running:** fAIrewall runs in the background. Closing the window minimizes it to the system tray — it does not quit. To fully quit, right-click the tray icon and select **Quit fAIrewall**.

---

## 3. Chrome Extension

### Requirements

- Google Chrome (version 120 or later) or Microsoft Edge (Chromium-based)
- fAIrewall desktop app must be installed and running

### Step-by-step (Chrome Web Store)

> *Chrome Web Store listing is pending approval. Use the manual method below until the extension is published.*

1. Open the Chrome Web Store link (will be available at [fairewall.ai/download](https://fairewall.ai/download))
2. Click **Add to Chrome**
3. Confirm by clicking **Add extension** in the popup
4. The fAIrewall shield icon will appear in your Chrome toolbar

### Step-by-step (Manual / Developer Mode)

Use this method if the extension is not yet on the Chrome Web Store:

1. **Download** the extension `.zip` from [fairewall.ai/download](https://fairewall.ai/download) and extract it to a folder on your computer.

2. **Open Chrome** and navigate to `chrome://extensions/` in the address bar.

3. **Enable Developer Mode** using the toggle in the top-right corner of the extensions page.

4. **Click "Load unpacked"** and select the extracted extension folder (the one containing `manifest.json`).

5. **Pin the extension:** Click the puzzle piece icon in the Chrome toolbar, find fAIrewall, and click the pin icon to keep it visible.

6. **Verify connection:** Open the fAIrewall desktop app. The **Chrome Extension** section should show **Connected** with a green indicator.

### Edge installation

The same extension works on Microsoft Edge:

1. Open `edge://extensions/` in the address bar
2. Enable **Developer Mode** (bottom-left toggle)
3. Click **Load unpacked** and select the extension folder
4. The extension works identically to the Chrome version

---

## 4. Verify Your Installation

After installing both components, run through this quick checklist:

### Checklist

- [ ] **Desktop app is running** — Shield icon visible in menu bar (macOS) or system tray (Windows)
- [ ] **Extension is connected** — Desktop app shows "Chrome Extension: Connected"
- [ ] **Protection is ON** — Extension popup shows "Protection: ON"
- [ ] **Test prompt** — Go to [chatgpt.com](https://chatgpt.com) and type a test prompt containing a fake email like `test@example.com`. After sending, the fAIrewall overlay should briefly appear at the bottom-right confirming the prompt was protected.
- [ ] **Check the dashboard** — Open the fAIrewall desktop app. The main view should show "1" under "Prompts" and the last activity section should show the redaction.

If all five checks pass, fAIrewall is fully operational.

---

## 5. Important Information

### Free Trial

Your 14-day free trial starts automatically on the first successful launch of the desktop app, once the local protection service is running. No sign-up or credit card is required.

Trial data is stored in your operating system's secure storage (macOS Keychain / Windows Credential Manager), which helps resist tampering.

When the trial expires and Protection is ON, protected prompts are blocked. Your audit logs and settings are preserved.

To learn more about licensing options, visit [fairewall.ai](https://fairewall.ai/#pricing).

### Protection OFF

When Protection is OFF, prompts are sent directly to AI providers without any PII scanning. fAIrewall does not process or log these prompts.

You can toggle Protection ON/OFF from the extension popup at any time.

### Privacy

All PII detection and masking happens locally on your device. No prompt data is ever sent to fAIrewall servers or any third party. Your audit logs are encrypted and stored locally using AES-256 encryption.

---

## Troubleshooting

### "Extension not connected"

- Make sure the fAIrewall desktop app is running (check for the tray icon)
- Refresh the AI provider page in Chrome
- If using manual install, ensure the extension is enabled in `chrome://extensions/`

### "BLOCKED" overlay appears

- **If trial expired:** Your 14-day trial has ended. Learn more at [fairewall.ai](https://fairewall.ai)
- **If in Strict mode:** The desktop app must be running for prompts to be sent. Open the desktop app.

### Prompts not being scanned

- Check that Protection is **ON** in the extension popup
- Make sure you are on a supported AI provider: ChatGPT, Claude, DeepSeek, or Gemini
- Try refreshing the page

### macOS: "App is damaged" or cannot be opened

This should not happen with the notarized build. If it does:
1. Open **System Preferences → Privacy & Security**
2. Scroll down to find the fAIrewall entry
3. Click **Open Anyway**

### Windows: SmartScreen warning

This is expected until an EV code signing certificate is obtained. Click **More info → Run anyway** to proceed. The app is safe.

---

## Need Help?

- **Documentation:** [fairewall.ai/docs](https://fairewall.ai/docs)
- **Support:** [support@fairewall.ai](mailto:support@fairewall.ai)
- **Security issues:** [security@fairewall.ai](mailto:security@fairewall.ai)
