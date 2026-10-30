# ⚡ Yoda Bot v2.0 — Desktop Official User Guide
### High-Performance Dokkan Battle Automation Engine for Windows 10/11 & Linux x64

---

## 🌟 Overview

**Yoda Bot v2.0** is the next-generation, high-speed automation engine for *Dragon Ball Z: Dokkan Battle* (Global & Japan). Rebuilt from the ground up with a standardized interactive CLI, native Chrome DevTools Protocol (CDP) Google auto-login, and a browser-based APEX Web GUI, Yoda Bot offers full control over your box, farming, and card upgrades without manual friction.

### Key Highlights
- **Universal Multi-Platform Core**: Clean, standalone native builds tailored specifically for Windows 10/11 and Linux x64.
- **Game Engine Auto-Update**: Automatically detects Dokkan Battle client updates, updating API version codes and request hashes on the fly without breaking your workflow.
- **Interactive APEX Web GUI**: Full card management interface in your browser (`http://127.0.0.1:8080`) featuring 1-Click Awakening, 100% Potential, and instant SA maxing.
- **Native Browser Google Auto-Login (CDP)**: Seamless account linking and login using your installed browser (Chrome, Edge, Brave)—no ChromeDriver downloads or third-party proxies required.

---

## 🚀 Windows 10 / 11 Quick Start

The Windows release package is fully self-contained and pre-configured to eliminate all common Windows 11 Smart App Control (SAC) and execution policy issues.

### 1. Extraction
1. Download `yodabot_2.0_windows.zip`.
2. Extract the archive into any folder of your choice (e.g., `C:\YodaBot\` or `Desktop\YodaBot\`).
   > *Note: Avoid extracting directly into root `C:\` or system folders requiring elevated Administrator permissions.*

### 2. Launching the Bot
- Simply **double-click** `Launch_Windows.py` in Windows Explorer, or open your terminal inside the folder and run:
  ```cmd
  py Launch_Windows.py
  ```

### 🛡️ What `Launch_Windows.py` Does Automatically For You:
- **Smart App Control & MOTW Bypass**: Strips Windows Mark-of-the-Web (`Zone.Identifier`) metadata from all extracted files to prevent Windows 11 Smart App Control from falsely blocking Python scripts.
- **Legacy Python Cleaner**: Detects and cleanly uninstalls outdated Python 3.9 installations if present.
- **Automatic Python 3.12 Runtime**: Checks if Python 3.12 64-bit is available on your machine; if missing, it downloads and installs official Python 3.12.3 silently.
- **Self-Healing Virtual Environment**: Generates an isolated `venv/` and installs all necessary dependencies automatically using `python.exe -m pip`. You never need to manage `pip` manually.

---

## 🐧 Linux (Ubuntu / Debian x64) Quick Start

The Linux release package features native Cython-compiled binaries (`.so`) optimized for 64-bit Linux distributions (Ubuntu 20.04+, Debian 11+, Fedora, Arch).

### 1. Extraction
```bash
unzip yodabot_2.0_linux.zip -d ~/yodabot
cd ~/yodabot
```

### 2. Launching the Bot
You have two launch options:

- **Interactive CLI (Standard)**:
  ```bash
  bash launch_linux.sh
  ```
- **Direct Web GUI Launcher**:
  ```bash
  bash start_gui.sh
  ```
  *(Starts the background Uvicorn server and automatically opens `http://127.0.0.1:8080` in your default Linux desktop browser).*

---

## 🔐 First-Time Discord Verification

Yoda Bot uses Discord OAuth2 to authenticate your access tier (`VIP` or `APEX`) linked to the official Yoda Community.

1. On your very first start, the bot will display the login menu:
   ```text
   🔐 No active session found. Choose how to log in:
      1) Dev Mode (developer password)
      2) Discord login (normal)
      Option [1/2]: 
   ```
2. Type **`2`** and press **Enter**.
3. A local verification server will spin up and open your browser automatically to:
   ```text
   http://localhost:5000/login
   ```
4. Click **Authorize** on Discord.
5. Once your account role is validated, your browser displays **`Access Granted`**, and the bot stores your encrypted session into `subscriptions.json`.
6. **You will never have to log in again on this machine**—future launches will immediately boot straight to the Yoda Bot menu!

---

## 🎮 Account Setup & Google Auto-Login (CDP)

Once inside the interactive prompt (`YODA $`), you can initialize or switch Dokkan accounts easily:

### 1. Creating or Loading Accounts
- **`new`**: Guides you through generating a fresh Dokkan Battle account, completing the tutorial automatically, and setting up the account for farming.
- **`load`**: Loads an existing account profile saved in the `saves/` folder.
- **`transfer`**: Transfers an existing account into Yoda Bot via transfer code or Google authentication.

### 2. Google Auto-Login via Chrome DevTools Protocol (CDP)
Traditional bots often fail or crash during Google login due to outdated ChromeDriver mismatches or Google blocking automated browser sessions. **Yoda Bot v2.0 solves this natively:**

- **Zero-Dependency CDP**: Communicates directly with your locally installed Chromium browser (Google Chrome, Microsoft Edge, Brave) via native WebSocket Chrome DevTools Protocol.
- **No ChromeDriver Required**: You never need to download or update ChromeDriver.
- **How to Use**:
  1. Run `transfer` or `link` and select Google Login.
  2. Yoda Bot launches your default browser in stealth mode.
  3. Sign in to your Google Account and click **Allow**.
  4. Yoda Bot intercepts the OAuth callback (`com.googleusercontent.apps...`) directly from browser network events and completes the handshake instantly!

---

## ⌨️ Main CLI Commands & The 2x Enter Rule

All Yoda Bot CLI commands are **case-insensitive** and use standard `snake_case`.

| Command | Description |
| :--- | :--- |
| `info` | Displays comprehensive account status: Rank, Dragon Stones, Zeni, Stamina, Card Box capacity, and active Deck. |
| `help` | Prints detailed manual and usage instructions for all available commands. |
| `omega_farm` | The master automation runner. Sequentially farms Quest Mode, Story Events, Medals, and Missions. |
| `db_story_all` | Clears all available Dragon Ball Story stages and sub-difficulties, claiming all first-clear Dragon Stones. |
| `kagi` | **Portal of Memories** farmer. Supports individual or multiple stage IDs separated by spaces or commas (e.g. `kagi 101001, 101002 101003`). |
| `mission` / `auto_mission` | Automatically scans, completes, and claims all pending daily, event, and Z-mission rewards. |
| `smart_team` | AI-driven team builder: analyzes stage requirements, enemy types, and category boosts to assemble optimal teams. |
| `deck_change` | Switch active team slots, replace leaders, or customize card slots. |
| `eza_run` / `eza` | Automatically farms Extreme Z-Battle stages from Level 1 up to Level 30+ for Dragon Stones, Kais, and Awakening Medals. |
| `clash` | Fully automates Ultimate Clash (Battlefield), selecting optimal mono/category teams per boss. |
| `gui` | Spawns the interactive APEX Web GUI in your browser. |

### 💡 The 2x Enter Rule (Quick Menu Return)
Whenever you are inside a command or sub-prompt and wish to exit or reset:
- Press **Enter** once: the bot displays `[Press Enter again to clear screen & return to menu]`.
- Press **Enter** a second time: the bot instantly wipes the screen buffer and displays the clean main menu.

---

## 🚀 The Star Feature: Interactive Web GUI (`gui`)

Type **`gui`** into the terminal to unlock Yoda Bot’s visual powerhouse. The bot starts a local FastAPI/Uvicorn server and launches your browser at **`http://127.0.0.1:8080`**.

```text
YODA $ gui
[Web GUI] Server running on http://127.0.0.1:8080 (GUI active in background — CLI ready for commands).
```

### Powerful Web Features:
1. **Intelligent Box Organization**:
   - Sort cards by **Release (Newest)**, Rarity, Level, or Type.
   - Quick one-click filters: **`LR`**, **`UR`**, **`EZA`**, **`SEZA`**, and **`Extra Dupes`**.
2. **1-Click Max Level & SA 10**:
   - Maximize any unit’s level and Super Attack level instantly without navigating training screens.
3. **1-Click 100% Hidden Potential `[APEX]`**:
   - Automatically unlocks all 4 Hidden Potential paths (Top-Left, Top-Right, Bottom-Left, Bottom-Right) and activates all orb nodes with optimal skill distribution (Crit / Additional / Dodge) in one single tap.
4. **Step-by-Step 1-Click Dokkan Awaken**:
   - Select any UR or SSR card; the bot checks current medal inventory, determines the required Dokkan Event stages, farms missing medals, and awakens the card step-by-step up to its final LR state.
   - **Interactive Stamina Refill Prompt**: If your Stamina runs out during medal farming, an interactive modal appears in your browser asking if you wish to spend 1 Dragon Stone to refill Stamina. Upon confirmation, farming resumes smoothly without restarting.
5. **1-Click EZA & Super EZA (SEZA)**:
   - Takes your awakened units and clears their respective Extreme Z-Battles automatically to complete their full EZA/SEZA steps.
6. **Bulk Dupe Cleaner (Zeni / Baba)**:
   - Safely identifies excess unneeded copies of units whose paths are already unlocked, letting you bulk-convert them into Zeni or Baba Points with a single confirmation.

---

## ❓ Troubleshooting & Support

- **Browser doesn't open automatically?**
  - Manually open your browser and navigate to `http://127.0.0.1:8080` (for GUI) or `http://localhost:5000/login` (for Discord Auth).
- **Windows Smart App Control warning?**
  - Ensure you ran `Launch_Windows.py` using standard Windows Python launcher. It unblocks extracted files automatically.
- **Need help or want to join the community?**
  - Join our official Discord server for updates, guides, and support!
