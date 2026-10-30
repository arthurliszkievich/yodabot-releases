# 📱 Yoda Bot v2.0 — Android / Mobile Official Guide
### Complete Dokkan Battle Automation Engine for Android (Termux ARM64) & `yoda-auth-helper.apk`

---

## 🌟 Overview

**Yoda Bot v2.0 Mobile** brings the complete desktop-grade Dokkan Battle automation suite directly to your Android smartphone or tablet. By leveraging the power of **Termux (ARM64)** and our dedicated **`yoda-auth-helper.apk`** companion app, you can farm Dragon Stones, 100% Hidden Potential cards, Dokkan Awaken units, and clean your box on the go—with zero PC required!

### Key Highlights
- **Direct on Phone**: Runs locally on Android ARM64 devices without root.
- **Full Touch Web GUI**: Control your box using an intuitive mobile-friendly touch interface in Chrome or Brave (`http://127.0.0.1:8080`).
- **Frictionless Setup**: Automated `mobile_setup.sh` installs Python, native packages, and isolates dependencies without complex compile steps.
- **Automated Google Login via APK**: Our custom lightweight `yoda-auth-helper.apk` intercepts Google OAuth callbacks directly inside Android, giving you seamless, 100% automatic Google account login on mobile.

---

## 📥 Step 1: Installing Prerequisites & Yoda Auth Helper APK

Before extracting Yoda Bot, install the three required Android components:

### 1. Install Termux & Termux:API
> [!IMPORTANT]
> **DO NOT install Termux from Google Play Store!** The Play Store version is abandoned and outdated.
> Always install from **F-Droid** or official **GitHub Releases**:
> - [Termux on F-Droid](https://f-droid.org/packages/com.termux/) or [Termux GitHub](https://github.com/termux/termux-app/releases)
> - [Termux:API on F-Droid](https://f-droid.org/packages/com.termux.api/) or [Termux:API GitHub](https://github.com/termux/termux-api/releases)

### 2. Install `yoda-auth-helper.apk`
1. Download **`yoda-auth-helper.apk`** from the Yoda Bot v2.0 Release page onto your Android device.
2. Open the downloaded APK and tap **Install** (allow "Install Unknown Apps" if prompted by Android).

### 🔍 Why is `yoda-auth-helper.apk` Needed?
On Android, Google OAuth2 redirects using a proprietary custom URI scheme:
```text
com.googleusercontent.apps.33528429135-fg507svof8s85i1c32isr6ci5radpqqh:/oauth2callback?code=...
```
Because standard terminal environments like Termux cannot natively register Android deep-link scheme filters, mobile Google logins would normally fail with a browser error. 

**`yoda-auth-helper.apk` solves this completely:**
- It registers an Android Intent Filter for the Dokkan Google OAuth scheme.
- When you authenticate your Google Account in Chrome, the helper app catches the callback instantly.
- It grabs the authorization code and delivers it straight to Yoda Bot in Termux automatically.
- **Result:** 100% automated, zero-headache Google account linking on Android!

---

## ⚙️ Step 2: Extracting & First-Time Setup in Termux

1. Open the **Termux** app on your phone.
2. Grant Termux permission to access your storage by running:
   ```bash
   termux-setup-storage
   ```
   *(Tap **Allow** on the Android popup).*

3. Extract `yodabot_2.0_mobile.zip` from your Downloads folder into Termux:
   ```bash
   unzip ~/storage/downloads/yodabot_2.0_mobile.zip -d ~/yodabot && cd ~/yodabot
   ```

4. Run the automated zero-friction mobile setup:
   ```bash
   bash mobile_setup.sh
   ```
   **What `mobile_setup.sh` does automatically:**
   - Detects the Termux ARM64 environment.
   - Installs pre-compiled native packages (`pkg install python clang libjpeg-turbo...`) to avoid painful local C/Rust compilations.
   - Creates an isolated virtual environment (`dokbot/`) with system site packages enabled.
   - Injects a global **`yoda`** executable command directly into `$PREFIX/bin`, allowing you to launch the bot from any folder at any time.

---

## 🚀 Step 3: Launching the Bot & Discord Verification

Once the setup finishes:

1. Launch Yoda Bot by typing either:
   ```bash
   yoda
   ```
   *(or `bash launch_unix.sh` inside the `~/yodabot` directory).*

2. **First-Time Discord Verification**:
   On your first launch, the bot presents the login options:
   ```text
   🔐 No active session found. Choose how to log in:
      1) Dev Mode (developer password)
      2) Discord login (normal)
      Option [1/2]: 
   ```
   - Type **`2`** and press **Enter**.
   - A local server starts and prompts you to authenticate via Discord at `http://localhost:5000/login`.
   - Your phone browser opens (or tap the link in Termux) and click **Authorize** on Discord.
   - Once validated, the screen shows **`Access Granted`**, and your credentials are saved permanently in `subscriptions.json`. You will not need to authenticate again!

---

## 📱 Step 4: Using the Touch Web GUI (`gui`) on Your Phone

You don't have to manage complex card IDs in the command line on a tiny keyboard. Yoda Bot v2.0 includes a full touch-friendly Web GUI!

1. In Termux, at the `YODA $` prompt, simply type:
   ```text
   gui
   ```
2. The bot starts the background server and displays:
   ```text
   [Web GUI] Server running on http://127.0.0.1:8080 (GUI active in background — CLI ready for commands).
   ```
3. Open **Google Chrome** or **Brave** on your Android device and navigate to:
   ```text
   http://127.0.0.1:8080
   ```

### Touchscreen 1-Click Operations:
- **Card Sorting & Filters**: Tap **`LR`**, **`UR`**, **`EZA`**, **`SEZA`**, or **`Extra Dupes`** to immediately filter your collection.
- **1-Click Max Level & SA 10**: Tap any card and max out level and Super Attack instantly.
- **1-Click 100% Hidden Potential `[APEX]`**: Unlocks all 4 branches and fully fills out orbs and skills with a single tap.
- **1-Click Step-by-Step Dokkan Awaken**: Checks your medals, automatically runs the required Dokkan Events, and awakens your card to LR.
  - *Stamina Refill Notification*: If your Stamina is depleted, a responsive mobile dialog appears asking if you want to spend 1 Dragon Stone to refill Stamina, resuming the run seamlessly.
- **1-Click EZA / SEZA**: Complete all 30/10 stages to maximize the unit's Extreme Z-Awakened passive and stats.
- **Bulk Dupe Cleaner (Zeni / Baba)**: Clear out excess unlocked duplicate SSRs and SRs for massive Baba Points or Zeni with one touch.

---

## ⌨️ Fast CLI Reference & Tips

All commands are case-insensitive:

- `info`: Check current Dragon Stones, Zeni, Stamina, and active deck.
- `help`: Full list of CLI commands and arguments.
- `omega_farm`: Complete master farming suite (Quests, Stories, Events).
- `db_story_all`: Clears all Dragon Ball Story stages for easy Dragon Stones.
- `kagi`: Portal of Memories farmer. Accepts multiple stage IDs (e.g. `kagi 101001, 101002 101003`).
- `mission` / `auto_mission`: Automatically claim all completed mission rewards.
- `smart_team`: AI-generated team builder optimized for whatever stage you are tackling.
- `deck_change`: Manage your 6 team slots.
- `eza_run`: Auto-farm any Extreme Z-Battle.
- `clash`: Complete all stages of Ultimate Clash (Battlefield).

### 💡 The 2x Enter Rule
If you are inside a command loop or wish to clear your phone screen back to the main menu:
- Press **Enter** once (prompts to confirm).
- Press **Enter** again: immediately clears the Termux terminal and shows the clean main menu.

---

## ❓ Frequently Asked Questions (FAQ)

- **Q: Do I need to root my Android phone?**
  - **A:** Absolutely not. Termux and `yoda-auth-helper.apk` run in regular user space without any root permissions required.
- **Q: Does Yoda Bot keep running if I switch apps?**
  - **A:** Yes. Make sure to pull down your Android notification drawer and tap **"Acquire Wakelock"** in Termux so Android doesn't put Termux to sleep when you switch to your browser.
- **Q: Can I use both the CLI and Web GUI at the same time?**
  - **A:** Yes! The Web GUI runs in a background thread, leaving the Termux CLI responsive for commands.
