# 📱 Yoda Bot v2.0 — Android / Mobile Official Guide
### Complete Dokkan Battle Automation Engine for Android (Termux ARM64) & `yoda-auth-helper.apk`

---

## 🌟 Overview

**Yoda Bot v2.0 Mobile** brings the complete desktop-grade Dokkan Battle automation suite directly to your Android smartphone or tablet. By leveraging the power of **Termux (ARM64)** and our dedicated **`yoda-auth-helper.apk`** companion app, you can farm Dragon Stones, 100% Hidden Potential cards, Dokkan Awaken units, and clean your box on the go—with zero PC required!

### Key Highlights
- **Direct on Phone**: Runs locally on Android ARM64 devices without root.
- **Auto Browser Redirection**: Opening Web GUI (`gui`), Discord login, or Google account transfer (`transfer`) automatically launches your Android browser on screen without manual URL copying!
- **Zero-Friction Mobile Setup**: Automated `mobile_setup.sh` repairs base packages, installs pre-compiled native ARM64 wheels, and isolates dependencies without complex C/Rust compilation.
- **Automated Google Login via APK**: Our custom lightweight `yoda-auth-helper.apk` catches Google OAuth redirects and delivers the code straight to your clipboard, giving you seamless 1-tap Google account transfer on mobile.

---

## 📥 Step 1: Installing Prerequisites & Yoda Auth Helper APK

Before extracting Yoda Bot, install the three required Android components:

### 1. Install Termux & Termux:API
> [!IMPORTANT]
> **DO NOT install Termux from Google Play Store!** The Play Store version is abandoned and outdated.
> Always install from **F-Droid** or official **GitHub Releases**:
> - [Termux on F-Droid](https://f-droid.org/packages/com.termux/) or [Termux GitHub Releases](https://github.com/termux/termux-app/releases)
> - [Termux:API on F-Droid](https://f-droid.org/packages/com.termux.api/) or [Termux:API GitHub Releases](https://github.com/termux/termux-api/releases)

### 2. Install `yoda-auth-helper.apk`
1. Download **`yoda-auth-helper.apk`** from the Yoda Bot v2.0 Release page onto your Android device:
   - 🔗 [Download yoda-auth-helper.apk](https://github.com/arthurliszkievich/yodabot-releases/releases/download/v2.0.0/yoda-auth-helper.apk)
2. Open the downloaded APK and tap **Install** (allow *"Install Unknown Apps"* in Android Settings if prompted).

### 🔍 Why is `yoda-auth-helper.apk` Needed?
On Android, Google OAuth2 redirects using a custom URI scheme (`com.googleusercontent.apps...:/oauth2callback`). Terminal apps cannot intercept Android deep-links directly. 

**`yoda-auth-helper.apk` solves this completely:**
- It registers an Android Intent Filter for the Dokkan Google OAuth scheme.
- When you authenticate your Google Account in Chrome or Brave, the helper app catches the callback instantly.
- It copies the authorization code to your clipboard and notifies you via Toast.
- Termux detects it automatically—you just tap **Enter** to link your account!

---

## ⚙️ Step 2: Extracting & Running Mobile Setup in Termux

1. Open the **Termux** app on your phone.
2. Grant Termux permission to access your storage:
   ```bash
   termux-setup-storage
   ```
   *(Tap **Allow** on the Android popup).*

3. Unpack `yodabot_2.0_mobile.zip` into `~/yodabot`:
   ```bash
   pkg install -y unzip
   mkdir -p ~/yodabot && unzip -o ~/storage/downloads/yodabot_2.0_mobile.zip -d ~/yodabot
   cd ~/yodabot/yodabot_2.0_mobile 2>/dev/null || cd ~/yodabot
   ```

4. Run the automated zero-friction mobile setup:
   ```bash
   bash mobile_setup.sh
   ```

**What `mobile_setup.sh` does automatically:**
- Unjams and upgrades base Termux packages with `apt-get`.
- Installs pre-compiled native ARM64 packages (`python`, `clang`, `make`, `libffi`, `openssl`, `termux-tools`, `termux-api`, `python-pycryptodome`, `python-pillow`).
- Bypasses slow Rust compilation by installing pre-built `pydantic-core` from the Termux User Repository.
- Creates an isolated Python virtual environment (`dokbot/`) with system site packages enabled.
- Injects a global **`yoda`** command directly into `$PREFIX/bin`, allowing you to launch the bot from any directory.

---

## 🚀 Step 3: Launching the Bot & Discord Verification

Once the setup completes:

1. Launch Yoda Bot by simply typing:
   ```bash
   yoda
   ```
   *(or `bash launch_unix.sh` inside the installation folder).*

2. **First-Time Discord Verification**:
   On your first launch, the bot presents the login options:
   ```text
   🔐 No active session found. Choose how to log in:
      1) Dev Mode (developer password)
      2) Discord login (normal)
      Option [1/2]: 
   ```
   - Type **`2`** and press **Enter**.
   - Your Android phone browser **automatically opens** to the Discord authorization page.
   - Tap **Authorize** on Discord.
   - Once validated, the screen displays **`Access Granted`**, and your credentials are saved permanently in `subscriptions.json`. You will not need to authenticate again!

---

## 📱 Step 4: Using the Touch Web GUI (`gui`) on Mobile

Yoda Bot v2.0 includes a full mobile-friendly touch interface:

1. In Termux at the `YODA $` prompt, simply type:
   ```text
   gui
   ```
2. Your phone's default browser **automatically opens** directly to:
   ```text
   http://127.0.0.1:8080
   ```
3. The Web GUI runs in the background while the Termux CLI remains available for commands.

### Mobile Touch Features:
- **Card Sorting & Filters**: Tap **`LR`**, **`UR`**, **`EZA`**, **`SEZA`**, or **`Extra Dupes`** to immediately filter your collection.
- **1-Click Max Level & SA 10**: Tap any card and max out level and Super Attack instantly.
- **1-Click 100% Hidden Potential `[APEX]`**: Unlocks all 4 branches and fully fills out orbs and skills with a single tap.
- **1-Click Dokkan Awaken**: Checks your medals, automatically runs the required Dokkan Events, and awakens your card to TUR / LR.
- **1-Click Super EZA / EZA**: Complete all 30/10 stages to maximize the unit's Extreme Z-Awakened passive and stats.
- **Bulk Dupe Cleaner (Zeni / Baba)**: Clear out excess unlocked duplicate SSRs and SRs for massive Baba Points or Zeni with one touch.

---

## 🔄 Step 5: Transferring a Google Account (`transfer`)

1. In Termux, type:
   ```text
   transfer
   ```
2. Choose account name and platform (`1` for Android).
3. The bot **automatically opens Google login** in your default mobile browser.
4. Sign in to your Google Account and tap **Allow**.
5. `yoda-auth-helper.apk` catches the callback and copies the token to your clipboard.
6. Return to Termux and simply press **Enter** (or paste if preferred). The bot imports and saves your game account immediately!

---

## ⌨️ Fast CLI Reference & Tips

Yoda Bot provides a complete suite of automated commands for mobile farming, missions, and team optimization.

📖 **[Click here for the Full Command Reference (COMMANDS.md)](./COMMANDS.md)**

### 💡 Android Tips:
- **Acquire Wakelock**: Pull down your Android notification drawer and tap **"Acquire Wakelock"** in Termux so Android's battery optimizer does not sleep the bot when you switch to other apps.
- **The 2x Enter Rule**: If you are inside a command loop or wish to clear your phone screen back to the main menu, press **Enter** twice to clear the terminal and return to the main menu.

---

## ❓ Frequently Asked Questions (FAQ)

- **Q: Do I need to root my Android phone?**
  - **A:** Absolutely not. Termux and `yoda-auth-helper.apk` run in regular user space without any root permissions required.
- **Q: What if Termux gives `bash: mobile_setup.sh: No such file or directory`?**
  - **A:** Make sure you enter the extracted folder: `cd ~/yodabot/yodabot_2.0_mobile 2>/dev/null || cd ~/yodabot` and run `bash mobile_setup.sh`.
- **Q: Does Yoda Bot keep running if I switch apps?**
  - **A:** Yes, as long as you tap **"Acquire Wakelock"** in the Termux notification.
- **Q: Can I use both the CLI and Web GUI at the same time?**
  - **A:** Yes! The Web GUI runs in a background thread, leaving the Termux CLI ready for commands.
